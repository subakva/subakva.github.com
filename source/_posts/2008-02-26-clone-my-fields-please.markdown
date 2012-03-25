---
date: '2008-02-26 23:50:59'
layout: post
slug: clone-my-fields-please
status: publish
title: Clone My Fields, Please
wordpress_id: '16'
tags:
- bugs
- django
- django search
- python
---

### The Introduction





I recently started using the SearchManager from [the Mercury Tide white paper](http://www.mercurytide.co.uk/whitepapers/django-full-text-search/) on using [MySQL full-text search](http://dev.mysql.com/doc/refman/5.0/en/fulltext-search.html) with [Django](http://www.djangoproject.com/). It's been helpful, but I ran into a bug recently while trying to add a default filter to a SearchManager subclass.






### The Boring Context





Rather than deleting objects from the database, my application sets a boolean flag to indicate that the content is not longer relevant. I wanted my manager to apply a filter to every query set to include only items that are not disabled. Here's what the manager class looks like:





    
    
    class SearchableItemManager(SearchMangager):
        def __init__(self):
            zuper = super(SearchableItemManager, self)
            zuper.__init__(('name','description',))
    
        def get_query_set(self):
            query = super(SearchableItemManager, self).get_query_set()
            return query.filter(is_enabled=True)
    





### The Ugly Crash





When I made the change, I found that calling the `search()` method raised a TypeError: "'NoneType' object is not iterable." The error occurred when the SearchQuerySet tried to construct the SQL for the MATCH...AGAINST clause. Somehow, the `_search_fields` tuple on the SearchQuerySet was None.






### The Mystery Solved





This had me baffled until I had a look at the _QuerySet code in Django. It seems obvious now, but adding an additional filter to a query set returns a clone of the original with the new filter added. The _QuerySet object contains a `_clone` method that copies a hard-coded list of fields from the old QS to the new one. Naturally, that hard-coded list doesn't know anything about my `_search_fields`, so the property has no value on the clone.






### The Fix





Now, depending on how much of a zealot you are about modifying "private" functions, there are two ways to fix this. The easiest method is to simply override the `_clone` method and add the `_search_fields` tuple to the clone. The alternative is to override every method that depends on the _clone method, and copy over the `_search_fields` tuple for each one. I think that would be stupid, and will speak of it no further. Here's the code I added to generate happiness:





    
    
    class SearchQuerySet(models.query.QuerySet):
        # ... code from the original Mercury Tide class
        def _clone(self, klass=None, **kwargs):
            zuper = super(SearchQuerySet, self)
            clone = zuper._clone(klass, **kwargs)
            clone._search_fields = self._search_fields
            return clone
    



  *[QS]: Query Set
