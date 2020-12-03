<!--
https://readme42.com
-->


[![](https://img.shields.io/pypi/v/django-split-listview.svg?maxAge=3600)](https://pypi.org/project/django-split-listview/)
[![](https://img.shields.io/badge/License-Unlicense-blue.svg?longCache=True)](https://unlicense.org/)
[![](https://github.com/andrewp-as-is/django-split-listview.py/workflows/tests42/badge.svg)](https://github.com/andrewp-as-is/django-split-listview.py/actions)

### Installation
```bash
$ [sudo] pip install django-split-listview
```

#### Examples
```python
from django_split_listview.views import SplitListView

class RepoListView(SplitListView):
    def get_queryset_base(self):
        return self.model.all()

    def get_queryset_filter_kwargs(self):
        if self.request.GET.get('type','') == 'fork':
            return {'fork':True}

    def get_queryset_only_fields(self):
        return ['id','name','stargazers_count','language']

    def get_queryset_order_by_fields(self):
        if self.request.GET.get('o','') == 'stars':
            return ['-stargazers_count']
        return ['-updated_at']
```

<p align="center">
    <a href="https://readme42.com/">readme42.com</a>
</p>
