# dockerfile Odoo version 14.0 

## création de deux dossiers dans l'host :

1) dossier datas de la base de données postgresql 13.0 Odoo

D:/PG_datas/pg_odoo_v14 
relatif au dossier de la variable PGDATA de l'image docker de postgresql.


2) dossier datas de l'instance odoo utilisé 

D:/odoo14_docker 
relative au dossier odoo dans le conteneur docker


## creation du conteneur postgresql de la base de donnée d'odoo :

docker run -d -p 5432:5432 -v D:/PG_datas/pg_odoo_v14:/var/lib/postgresql/data -e POSTGRES_USER=odoo -e POSTGRES_PASSWORD=odoo -e POSTGRES_DB=postgres --name db postgres:13

## creation du conteneur de l'instance odoo en cours :


docker run -v D:/odoo14_docker:/var/lib/odoo -d -p 8069:8069 --name odoo --link db:db -t odoo:14.0



