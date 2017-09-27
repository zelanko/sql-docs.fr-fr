---
title: "L’exécution de la Console SSMA (SybaseToSQL) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Sybase Console,Database Connection Commands
- Sybase Console,Manageability Commands
- Sybase Console,Migration Commands
- Sybase Console,Migration Preparation Command
- Sybase Console,Project Commands
- Sybase Console,Report Commands
- Sybase Console,Script File Commands
- Sybase Console,Script Generation Commands
ms.assetid: ea8950b7-fabc-4aa4-89f8-9573a2617d70
caps.latest.revision: 22
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 0df634087870db32ed0357c97b1211d4fc1ddcba
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="executing-the-ssma-console-sybasetosql"></a>L’exécution de la Console SSMA (SybaseToSQL)
Microsoft vous fournit un ensemble robuste de script de commandes du fichier à exécuter et contrôler les activités SSMA. Les sections qui en découlent décrit en détail le même.  
  
## <a name="script-file-commands"></a>Commandes de fichier de script  
L’application console utilise certaines commandes de fichier de script standard comme énuméré dans cette section.  
  
## <a name="project-commands"></a>Commandes du projet  
Les commandes de projet gèrent la création de projets, ouvrir, enregistrer et les projets en cours de fermeture.  
  
### <a name="create-new-project"></a>créer à nouveau projet  
Crée un projet SSMA  
  
-   `project-folder`Indique le dossier du projet créé.  
  
-   `project-name`Indique le nom du projet. {string}  
  
-   `overwrite-if-exists`Attribut facultatif indique si un projet existant doit être remplacé. {valeur} booléenne  
  
-   `project-type:`Attribut facultatif. Indique le projet par exemple, « sql server 2005 » projet ou « sql server 2008 » projet ou projet de « sql server 2012 » ou « sql server 2014 » projet ou projet « sql azure ». Valeur par défaut est « sql server 2008 ».  
  
**Exemple :**  
  
```xml  
<create-new-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
  overwrite-if-exists="<true/false>" (optional)  
  
   project-type=”<sql-server-2008/sql-server-2005/sql-server-2012/sql-server-2014/sql-azure>”  
/>  
```  
Est de l’attribut 'Remplacer-if-exists' **false** par défaut.  
  
Est de l’attribut 'type de projet' **sql-server-2008** par défaut.  
  
### <a name="open-project"></a>projet ouvert  
  
-   `project-folder`Indique le dossier du projet créé. La commande échoue si le dossier spécifié n’existe pas.  {string}  
  
-   `project-name`Indique le nom du projet. La commande échoue si le projet spécifié n’existe pas.  {string}  
  
**Exemple de syntaxe :**  
  
```xml  
<open-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
/>  
```  
> [!NOTE]  
> SSMA pour Sybase Console Application prend en charge la compatibilité descendante. Vous ne pourrez pas ouvrir les projets créés par une version précédente de SSMA.  
  
### <a name="save-project"></a>enregistrer le projet  
Enregistre le projet de migration  
  
**Exemple de syntaxe :**  
  
```xml  
<save-project/>  
```  
  
### <a name="close-project"></a>projet de fermer  
Ferme le projet de migration  
  
**Exemple de syntaxe :**  
  
```xml  
<close-project   
  if-modified="<save/error/ignore>"   (optional)  
/>  
```  
Attribut 'if-modifié' est facultatif, **ignorer** par défaut.  
  
## <a name="database-connection-commands"></a>Commandes de connexion de base de données  
Les commandes de connexion de base de données aident à vous connecter à la base de données.  
  
> [!NOTE]  
> 1.  Le **Parcourir** fonctionnalité de l’interface utilisateur n’est pas prise en charge dans la console.  
> 2.  Pour plus d’informations sur « Créer des fichiers de Script », consultez [création de fichiers de Script &#40; SybaseToSQL &#41; ](../../ssma/sybase/creating-script-files-sybasetosql.md).  
  
### <a name="connect-source-database"></a>se connecter--base de données source  
  
-   Effectue la connexion à la base de données source et charge les métadonnées de niveau élevée de la base de données source mais pas toutes les métadonnées.  
  
-   Si la connexion à la source ne peut pas être établie, une erreur est générée et l’application console arrête davantage l’exécution  
  
Définition de serveur est récupérée à partir de l’attribut de nom défini pour chaque connexion dans la section serveur de fichier de connexion de serveur ou le fichier de script.  
  
**Exemple de syntaxe :**  
  
```xml  
<connect-source-database  server="<server-unique-name>"/>  
```  
  
### <a name="force-load-sourcetarget-database"></a>force-charge-source/cible-base de données  
  
-   Charge les métadonnées de la source.  
  
-   Utile pour travailler sur le projet de migration hors connexion.  
  
-   Si la connexion à la source/cible ne peut pas être établie, une erreur est générée et l’application console arrête davantage l’exécution  
  
Nécessite un ou plusieurs nœuds de la métabase en tant que paramètre de ligne de commande.  
  
**Exemple de syntaxe :**  
  
```xml  
<force-load metabase=”<source/target>” >  
  
  <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
  
### <a name="reconnect-source-database"></a>reconnecter--base de données source  
  
-   Se reconnecte à la base de données source mais ne se charge pas toutes les métadonnées, contrairement à la commande connect--base de données source.  
  
-   Si la (connexion avec la source re) ne peut pas être établie, une erreur est générée et l’application console arrête davantage l’exécution.  
  
**Exemple de syntaxe :**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
  
### <a name="connect-target-database"></a>se connecter--base de données cible  
  
-   Se connecte à la base de données SQL Server et charge entièrement les métadonnées de niveau élevée de la base de données cible mais pas les métadonnées.  
  
-   Si la connexion à la cible ne peut pas être établie, une erreur est générée et l’application console arrête davantage l’exécution.  
  
Définition de serveur est récupérée à partir de l’attribut de nom défini pour chaque connexion dans la section serveur de fichier de connexion de serveur ou le fichier de script  
  
**Exemple de syntaxe :**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
  
### <a name="reconnect-target-database"></a>reconnecter--base de données cible  
  
-   Se reconnecte à la base de données cible, mais ne se charge pas toutes les métadonnées, contrairement à la commande connect--base de données cible.  
  
-   Si la (connexion à la cible re) ne peut pas être établie, une erreur est générée et l’application console arrête davantage l’exécution.  
  
**Exemple de syntaxe :**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-commands"></a>Commandes de rapport  
Les commandes de rapports génèrent des rapports sur les performances de diverses activités de la Console de SSMA.  
  
### <a name="generate-assessment-report"></a>Générer--rapport d’évaluation  
  
-   Génère des rapports d’évaluation de la base de données source.  
  
-   Si la connexion de base de données source n’est pas effectuée avant d’exécuter cette commande, une erreur est générée et l’application console se ferme.  
  
-   Impossible de se connecter au serveur de base de données source lors de l’exécution de la commande, entraîne également à la fin de l’application console.  
  
-   `conversion-report-folder:`Spécifie le dossier où le rapport d’évaluation possible être stockées. (attribut facultatif)  
  
-   `object-name:`Spécifie l’ou les objets pris en compte pour la génération de rapports d’évaluation (il peut avoir les noms d’objet indivdual ou un nom d’objet de groupe).  
  
-   `object-type:`Spécifie le type de l’objet spécifié dans l’attribut de nom de l’objet (si la catégorie d’objet de type d’objet sera « catégorie » n’est spécifié).  
  
-   `conversion-report-overwrite:`Spécifie s’il faut remplacer le dossier de rapport d’évaluation s’il existe déjà.  
  
    **Valeur par défaut :** false. (attribut facultatif)  
  
-   `write-summary-report-to:`Spécifie le chemin d’accès où le rapport sera généré.  
  
    Si seul le chemin d’accès du dossier est indiqué, puis de fichiers par nom **AssessmentReport&lt;n&gt;. XML** est créé. (attribut facultatif)  
  
    La création de rapports a deux sous-catégories supplémentaires :  
  
    -   `report-errors`(= « true/false », valeur par défaut en tant que « false » (attributs facultatifs))  
  
    -   `verbose`(= « true/false », valeur par défaut en tant que « false » (attributs facultatifs))  
  
**Exemple de syntaxe :**  
  
```xml  
<generate-assessment-report  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"  
  
  write-summary-report-to="<file-name/folder-name>”             (optional)  
  
  verbose="<true/false>"                       (optional)  
  
  report-errors="<true/false>"                 (optional)  
  
  assessment-report-folder="<folder-name>"          (optional)  
  
  conversion-report-overwrite="<true/false>"   (optional)  
  
/>  
```  
ou  
  
```xml  
<generate-assessment-report  
  
  assessment-report-folder="<folder-name>"            (optional)  
  
  conversion-report-overwrite="<true/false>"     (optional)  
  
>  
<metabase-object object-name="<object-name>"  
  
        object-type="<object-category>"/>  
  
</generate-assessment-report>  
```  
  
## <a name="migration-commands"></a>Commandes de migration  
Les commandes de Migration de convertir le schéma de base de données cible au schéma source et migre les données vers le serveur cible.  
  
### <a name="convert-schema"></a>convertir le schéma  
  
-   Effectue une conversion de schéma à partir de la source vers le schéma cible.  
  
-   Si la connexion de base de données source ou cible n’est pas effectuée avant d’exécuter cette commande, ou la connexion au serveur de base de données source ou cible échoue pendant l’exécution de la commande, une erreur est générée et l’application console se ferme.  
  
-   `conversion-report-folder:`Spécifie le dossier où le rapport d’évaluation possible être stockées. (attribut facultatif)  
  
-   `object-name:`Spécifie l’ou les objets source pris en compte pour la conversion de schéma (il peut avoir les noms d’objet indivdual ou un nom d’objet de groupe).  
  
-   `object-type:`Spécifie le type de l’objet spécifié dans l’attribut de nom de l’objet (si la catégorie d’objet de type d’objet sera « catégorie » n’est spécifié).  
  
-   `conversion-report-overwrite:`Spécifie s’il faut remplacer le dossier de rapport d’évaluation s’il existe déjà.  
  
    **Valeur par défaut :** false. (attribut facultatif)  
  
-   `write-summary-report-to:`Spécifie le chemin d’accès où le rapport de synthèse est généré.  
  
    Si seul le chemin d’accès du dossier est indiqué, puis de fichiers par nom **SchemaConversionReport&lt;n&gt;. XML** est créé. (attribut facultatif)  
  
    La création de rapports a deux sous-catégories supplémentaires :  
  
    -   `report-errors`(= « true/false », valeur par défaut en tant que « false » (attributs facultatifs))  
  
    -   `verbose`(= « true/false », valeur par défaut en tant que « false » (attributs facultatifs))  
  
**Exemple de syntaxe :**  
  
```xml  
<convert-schema  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"  
  write-summary-report-to="<file-name/folder-name>"     (optional)  
  
  verbose="<true/false>"                          (optional)  
  
  report-errors="<true/false>"                    (optional)  
  
  conversion-report-folder="<folder-name>"             (optional)  
  
  conversion-report-overwrite="<true/false>"      (optional)  
  
/>  
```  
ou  
  
```xml  
<convert-schema  
  
  conversion-report-folder="<folder-name>"         (optional)  
  
  conversion-report-overwrite="<true/false>"> (optional)  
  
  <metabase-object object-name="<object-name>"  
  
    object-type="<object-category>"/>  
  
</convert-schema>  
```  
  
### <a name="migrate-data"></a>migrer des données  
Migre les données source à la cible.  
  
-   `object-name:`Spécifie l’ou les objets source pris en compte pour la migration de données (il peut avoir les noms d’objet indivdual ou un nom d’objet de groupe).  
  
-   `object-type:`Spécifie le type de l’objet spécifié dans l’attribut de nom de l’objet (si la catégorie d’objet de type d’objet sera « catégorie » n’est spécifié).  
  
-   `write-summary-report-to:`Spécifie le chemin d’accès où le rapport sera généré.  
  
    Si seul le chemin d’accès du dossier est indiqué, puis de fichiers par nom **DataMigrationReport&lt;n&gt;. XML** est créé. (attribut facultatif)  
  
    La création de rapports a deux sous-catégories supplémentaires :  
  
    -   `report-errors`(= « true/false », valeur par défaut en tant que « false » (attributs facultatifs))  
  
    -   `verbose`(= « true/false », valeur par défaut en tant que « false » (attributs facultatifs))  
  
**Exemple de syntaxe :**  
  
```xml  
<migrate-data  
  
  write-summary-report-to="<file-name/folder-name>"  
  
  report-errors="<true/false>" verbose="<true/false>">  
  
    <metabase-object object-name="<object-name>"/>  
  
    <metabase-object object-name="<object-name>"/>  
  
    <metabase-object object-name="<object-name>"/>  
  
    <data-migration-connection  
  
      source-use-last-used="true"/source-server="<server-unique-name>"  
  
      target-use-last-used="true"/target-server="<server-unique-name>"/>  
  
</migrate-data>  
```  
ou  
  
```xml  
<migrate-data  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"  
  
  write-summary-report-to="<file-name/folder-name>"  
  
  report-errors="<true/false>" verbose="<true/false>"/>  
```  
  
## <a name="migration-preparation-command"></a>Commande de préparation de migration  
La commande de préparation de Migration lance un mappage de schéma entre les bases de données source et cible.  
  
> [!NOTE]  
> La sortie de console par défaut définissant pour les commandes de migration est le rapport de sortie « Complète » avec aucun rapport d’erreur détaillé : résumé uniquement sur le nœud racine d’arborescence objet source.  
  
### <a name="map-schema"></a>schéma de mappage  
Mappage de schéma de base de données source vers le schéma cible.  
  
-   `source-schema`Spécifie le schéma source, que nous avons l’intention de migrer.  
  
-   `sql-server-schema`Spécifie le schéma cible que nous voulons être migrée.  
  
**Exemple de syntaxe :**  
  
```xml  
<map-schema source-schema="<source-schema>"  
  
sql-server-schema="<target-schema>"/>  
```  
  
## <a name="manageability-commands"></a>Commandes de la facilité de gestion  
Les commandes de la facilité de gestion permettent de synchroniser les objets de base de données cible avec la base de données source.  
  
> [!NOTE]  
> La sortie de console par défaut définissant pour les commandes de migration est le rapport de sortie « Complète » avec aucun rapport d’erreur détaillé : résumé uniquement sur le nœud racine d’arborescence objet source.  
  
### <a name="synchronize-target"></a>synchroniser la cible  
  
-   Synchronise les objets cibles avec la base de données cible.  
  
-   Si cette commande est exécutée sur la base de données source, une erreur s’est produite.  
  
-   Si la connexion de base de données cible n’est pas effectuée avant d’exécuter cette commande, ou la connexion au serveur de base de données cible échoue pendant l’exécution de la commande, une erreur est générée et l’application console se ferme.  
  
-   `object-name:`Spécifie l’ou les objets cible pris en compte pour la synchronisation avec la base de données cible (il peut avoir les noms d’objet indivdual ou un nom d’objet de groupe).  
  
-   `object-type:`Spécifie le type de l’objet spécifié dans l’attribut de nom de l’objet (si la catégorie d’objet de type d’objet sera « catégorie » n’est spécifié).  
  
-   `on-error:`Spécifie s’il faut spécifier des erreurs de synchronisation comme des avertissements ou erreurs. Options disponibles pour l’erreur :  
  
    -   total de rapports en tant qu’avertissement  
  
    -   rapport-chaque-sous-avertissement  
  
    -   Échec-script  
  
-   `report-errors-to:`Spécifie l’emplacement du rapport d’erreurs pour l’opération de synchronisation (attribut facultatif) si seul le chemin d’accès de dossier est indiqué, puis de fichiers par nom **TargetSynchronizationReport.XML** est créé.  
  
**Exemple de syntaxe :**  
  
```xml  
<synchronize-target  
  
object-name="<object-name>"  
  
on-error="<report-total-as-warning/  
  
report-each-as-warning/  
  
fail-script>" (optional)  
  
  report-errors-to="<file-name/folder-name>"        (optional)  
  
/>  
```  
ou  
  
```xml  
<synchronize-target  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"/>  
```  
ou  
  
```xml  
<synchronize-target>  
  
  <metabase-object object-name="<object-name>"/>  
  
  <metabase-object object-name="<object-name>"/>  
  
  <metabase-object object-name="<object-name>"/>  
  
</synchronize-target>  
```  
  
### <a name="refresh-from-database"></a>actualisation de base de données  
  
-   Actualise les objets de la source à partir de la base de données.  
  
-   Si cette commande est exécutée sur la base de données cible, une erreur est générée.  
  
Nécessite un ou plusieurs nœuds de la métabase en tant que paramètre de ligne de commande.  
  
-   `object-name:`Spécifie l’ou les objets source pris en compte pour l’actualisation à partir de la base de données source (il peut avoir les noms d’objet indivdual ou un nom d’objet de groupe).  
  
-   `object-type:`Spécifie le type de l’objet spécifié dans l’attribut de nom de l’objet (si la catégorie d’objet de type d’objet sera « catégorie » n’est spécifié).  
  
-   `on-error:`Spécifie s’il faut spécifier actualisation erreurs comme des avertissements ou erreurs. Options disponibles pour l’erreur :  
  
    -   total de rapports en tant qu’avertissement  
  
    -   rapport-chaque-sous-avertissement  
  
    -   Échec-script  
  
-   `report-errors-to:`Spécifie l’emplacement du rapport d’erreurs pour l’opération d’actualisation (attribut facultatif) si seul le chemin d’accès de dossier est indiqué, puis de fichiers par nom **SourceDBRefreshReport.XML** est créé.  
  
**Exemple de syntaxe :**  
  
```xml  
<refresh-from-database  
  
  object-name="<object-name>"  
  
  on-error="<report-total-as-warning/  
  
             report-each-as-warning/  
  
             fail-script>"              (optional)  
  
  report-errors-to="<file-name/folder-name>"        (optional)  
  
/>  
```  
ou  
  
```xml  
<refresh-from-database  
  
  object-name="<object-name>"  
  
  object-type="<object-category>" />  
```  
ou  
  
```xml  
<refresh-from-database>  
  
  <metabase-object object-name="<object-name>"/>  
  
</refresh-from-database>  
```  
  
## <a name="script-generation-commands"></a>Commandes de génération de script  
Les commandes de génération du Script effectuent deux tâches : ils permettent d’enregistrer la console de sortie dans un fichier de script ; et enregistrez la sortie de T-SQL dans la console ou un fichier basé sur le paramètre que vous spécifiez.  
  
### <a name="save-as-script"></a>en tant que script de sauvegarde  
Utilisé pour enregistrer les Scripts des objets dans un fichier mentionné lorsque la métabase = cible, il s’agit d’une alternative à la commande de synchronisation là où nous obtenir les scripts dans et exécutez le même sur la base de données cible.  
  
Nécessite un ou plusieurs nœuds de la métabase en tant que paramètre de ligne de commande.  
  
-   `object-name:`Spécifie l’ou les objets dont les scripts doivent être enregistrés. (Il peut avoir les noms d’objet indivdual ou un nom d’objet de groupe)  
  
-   `object-type:`Spécifie le type de l’objet spécifié dans l’attribut de nom de l’objet (si la catégorie d’objet de type d’objet sera « catégorie » n’est spécifié).  
  
-   `metabase:`Spécifie si elle Ile source ou une cible de la métabase.  
  
-   `destination:`Spécifie le chemin d’accès ou le dossier dans lequel le script doit être enregistré, si le nom de fichier n’est indiqué ensuite un nom de fichier dans le format (valeur de l’attribut object_name) .out  
  
-   `overwrite:`Si true elle remplace si le même nom de fichier existe. Il peut avoir les valeurs (true/false).  
  
**Exemple de syntaxe :**  
  
```xml  
<save-as-script  
  
  metabase="<source/target>"  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"  
  
  destination="<file-name/folder-name>"  
  
  overwrite="<true/false>"   (optional)  
  
/>  
```  
ou  
  
```xml  
<save-as-script  
  
  metabase="<source/target>"  
  
  destination="<file-name/folder-name>"  
  
    <metabase-object object-name="<object-name>"  
  
                     object-type="<object-category>"/>  
  
</save-as-script>  
```  
  
### <a name="convert-sql-statement"></a>instruction CONVERT-sql  
  
-   `context`Spécifie le nom du schéma.  
  
-   `destination`Spécifie si la sortie doit être stockée dans un fichier.  
  
    Si cet attribut n’est pas spécifié, l’instruction T-SQL convertie s’affiche sur la console. (attribut facultatif)  
  
-   `conversion-report-folder`Spécifie le dossier où le rapport d’évaluation possible être stockées. (attribut facultatif)  
  
-   `conversion-report-overwrite`Spécifie s’il faut remplacer le dossier de rapport d’évaluation s’il existe déjà.  
  
    **Valeur par défaut :** false. (attribut facultatif)  
  
-   `write-converted-sql-to`Spécifie le fichier (ou) le chemin d’accès du dossier où le code T-SQL converti est stocké. Lorsqu’un chemin d’accès du dossier est spécifié avec la `sql-files` attribut, chaque fichier source aura une cible correspondante fichier T-SQL créé sous le dossier spécifié. Lorsqu’un chemin d’accès du dossier est spécifié avec la `sql` attribut, le code T-SQL converti est écrit dans un fichier nommé Result.out sous le dossier spécifié.  
  
-   `sql`Spécifie les instructions sql de Sybase à convertir, une ou plusieurs instructions peuvent être séparés à utiliser un « ; »  
  
-   `sql-files`Spécifie le chemin d’accès des fichiers sql doit être converti en code T-SQL.  
  
-   `write-summary-report-to`Spécifie le chemin d’accès où le rapport de synthèse est généré. Si seul le chemin d’accès du dossier est indiqué, puis de fichiers par nom **ConvertSQLReport.XML** est créé. (attribut facultatif)  
  
    La création a 2 autres sous-catégories, notamment de rapport de synthèse viz..,:  
  
    -   erreurs de rapport (= « true/false », la valeur par défaut en tant que « false » (attributs facultatifs)).  
  
    -   verbose (= « true/false », valeur par défaut en tant que « false » (attributs facultatifs)).  
  
Nécessite un ou plusieurs nœuds de la métabase en tant que paramètre de ligne de commande.  
  
**Exemple de syntaxe :**  
  
```  
<convert-sql-statement  
  
       context="<database-name>.<schema-name>"  
  
        conversion-report-folder="<folder-name>"  
  
        conversion-report-overwrite="<true/false>"  
  
        write-summary-report-to="<file-name/folder-name>"   (optional)  
  
        verbose="<true/false>"   (optional)  
  
        report-errors="<true/false>"   (optional)  
  
        destination="<stdout/file>"   (optional)  
  
        write-converted-sql-to ="<file-name/folder-name>"  
  
        sql="SELECT 1 FROM DUAL;">  
  
    <output-window suppress-messages="<true/false>" />  
  
</convert-sql-statement>  
```  
ou  
  
```  
<convert-sql-statement  
  
         context="<database-name>.<schema-name>"  
  
         conversion-report-folder="<folder-name>"  
  
         conversion-report-overwrite="<true/false>"  
  
         write-summary-report-to="<file-name/folder-name>"   (optional)  
  
         verbose="<true/false>"   (optional)  
  
         report-errors="<true/false>"   (optional)  
  
         destination="<stdout/file>"   (optional)  
  
         write-converted-sql-to ="<file-name/folder-name>"  
  
         sql-files="<folder-name>\*.sql"  
  
/>  
```  
ou  
  
```  
<convert-sql-statement  
  
         context="<database-name>.<schema-name>"  
  
         conversion-report-folder="<folder-name>"  
  
         conversion-report-overwrite="<true/false>"  
  
         sql-files="<folder-name>\*.sql"  
  
/>  
```  
  
## <a name="next-step"></a>Étape suivante  
Pour plus d’informations sur les options de ligne de commande, consultez [les Options de ligne de commande dans la Console de SSMA &#40; SybaseToSQL &#41; ](../../ssma/sybase/command-line-options-in-ssma-console-sybasetosql.md) .  
  
Pour plus d’informations sur l’exemple de fichier de script console, consultez [fonctionne avec les exemples de fichiers de Script Console &#40; SybaseToSQL &#41;](../../ssma/sybase/working-with-the-sample-console-script-files-sybasetosql.md)  
  
L’étape suivante varie selon les spécifications de votre projet :  
  
-   Pour spécifier un mot de passe ou d’exportation / importation des mots de passe, consultez [la gestion des mots de passe &#40; SybaseToSQL &#41; ](../../ssma/sybase/managing-passwords-sybasetosql.md).  
  
-   Pour la génération de rapports, consultez [génération de rapports &#40; SybaseToSQL &#41; ](../../ssma/sybase/generating-reports-sybasetosql.md).  
  
-   Pour résoudre les problèmes dans la console, consultez [dépannage &#40; SybaseToSQL &#41; ](../../ssma/sybase/troubleshooting-sybasetosql.md).  
  

