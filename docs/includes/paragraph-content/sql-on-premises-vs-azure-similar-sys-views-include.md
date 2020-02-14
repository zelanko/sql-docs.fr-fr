
<!--
### Code examples for Azure cloud differ slightly from on-premises
  Or.....
### Code examples can differ for Azure SQL Database
-->

Certains exemples de code Transact-SQL écrits pour une instance locale de SQL Server ont besoin de changements mineurs pour s’exécuter sur le service Azure SQL Database dans le cloud. Une catégorie de ces exemples de code implique des vues système dont les préfixes de noms diffèrent légèrement entre les deux systèmes de base de données :

- **server\_** &nbsp; - &nbsp; _préfixe pour l’instance locale_
- **database\_** &nbsp; - &nbsp; _préfixe pour le service Azure SQL DB dans le cloud_

À titre d’illustration, le tableau suivant liste et compare deux sous-ensembles de vues système. Par souci de concision, les sous-ensembles sont limités aux noms de vues qui contiennent également la chaîne `_event`. Les sous-ensembles ont des préfixes de noms différents parce qu’ils proviennent de deux systèmes de bases de données différents.

| Nom de l’instance 2017 locale | Nom du service cloud |
| :------------------------- | :---------------------- |
| server_event_notifications<br />server_event_notifications<br />server_event_notifications<br />server_event_session_fields<br />server_event_session_targets<br />server_event_sessions<br />server_events<br />server_trigger_events | database_event_session_actions<br />database_event_session_events<br />database_event_session_fields<br />database_event_session_targets<br />database_event_sessions |
| &nbsp; | &nbsp; |

Les deux listes du tableau précédent sont exactes à compter de juin 2019. Toutefois, le contenu du tableau présenté ici peut devenir obsolète parce qu’il ne sera pas tenu à jour ici. Pour obtenir des listes exactes, exécutez l’instruction T-SQL SELECT suivante. Exécutez deux fois l’instruction SELECT : une fois sur chaque système de base de données.

```sql
SELECT name
    FROM sys.all_objects
    WHERE
        (name LIKE 'database\_%' { ESCAPE '\' } OR
         name LIKE 'server\_%' { ESCAPE '\' })
        AND name LIKE '%\_event%' { ESCAPE '\' }
        AND type = 'V'
    ORDER BY name;
```

<!--
The creation of this docs/includes/ file was prompted by Issue 2211 (https://github.com/MicrosoftDocs/sql-docs/issues/2211).
Initial PR was PR 10427 (https://github.com/MicrosoftDocs/sql-docs-pr/pull/10427).
The complaint was that a specific T-SQL code block failed on Azure SQL Database.

GeneMi  ,  2019/05/28
-->
