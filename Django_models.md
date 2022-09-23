## IMPS About Django Models ##

>> One to Many relationship in Django ORM

    When adding a Foreign Key Contraint in a model we add a parent Model to which we assign a Many to one or one to many relationship

    models.ForeginKey(Room, on_delete=models.SET_NULL)
        - models.SET_NULL : What this does when parent model is deleted we can set the set the childs to be set to NULL.
    
    models.ForeginKey(Room, on_delete=models.CASCADE)
        - When the Parent Model get Deleted all the Child related to the parent get deleted.

