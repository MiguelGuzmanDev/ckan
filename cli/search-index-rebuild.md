# search-index: Rebuild search index

En un esquema de balanceo de carga de Ckan con 2 nodos, se presentaron problemas al actualizar de la versión 2.10.0 > 2.10.1 (versión de parche), ya que una instancia me mostraba 15 conjuntos de datos y otra 5, por lo que intente reindexar:


```bash
ckan -c /etc/ckan/default/ckan.ini search-index rebuild
```

This default behaviour will refresh the index keeping the existing indexed datasets and rebuild it with all datasets. If you want to rebuild it for only one dataset, you can provide a dataset name

Pero esto no funciono, por lo que utilice el flag --clear:

```bash
ckan -c /etc/ckan/default/ckan.ini search-index rebuild -e --clear
```

El comando ckan search-index rebuild se utiliza en CKAN para reconstruir el índice de búsqueda de los conjuntos de datos y los recursos. El índice de búsqueda es esencial para permitir búsquedas rápidas y eficientes en el portal CKAN. El flag --clear es una opción que se puede utilizar con este comando para borrar el índice de búsqueda existente antes de volver a crearlo. Esto significa que todos los datos de índice anteriores se eliminarán y se generará un nuevo índice desde cero.

El uso del flag --clear es útil en situaciones en las que se necesita una reconstrucción completa del índice, por ejemplo, después de una importante actualización de CKAN o cuando se desea limpiar cualquier dato de índice antiguo y comenzar de nuevo