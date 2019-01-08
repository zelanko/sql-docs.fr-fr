---
title: Exécution de la Console SSMA (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/27/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
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
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 6cbdd0a1394114e3fdef0511c7ed14658f7dd9b0
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52406406"
---
# <a name="executing-the-ssma-console-sybasetosql"></a>Exécution de la console SSMA (SybaseToSQL)
Microsoft vous fournit un ensemble robuste de script de commandes de fichier pour exécuter et contrôler les activités SSMA. Les sections suivantes détaillent les mêmes.  
  
## <a name="script-file-commands"></a>Commandes de fichier de script  
L’application console utilise certaines commandes de fichier de script standard comme énuméré dans cette section.  
  
## <a name="project-commands"></a>Commandes de projet  
Les commandes de projet gèrent la création de projets, ouvrir, enregistrer et quitter des projets.  
  
### <a name="create-new-project"></a>Créer-nouveau projet  
Cette commande crée un nouveau projet SSMA.  
  
-   `project-folder` Indique le dossier du projet créé.  
  
-   `project-name` Indique le nom du projet. {string}  
  
-   `overwrite-if-exists`Attribut facultatif indique si un projet existant doit être remplacé. {valeur booléenne}  
  
-   `project-type:`Attribut facultatif. Indique le type de projet, qui est le projet « sql server 2005 » ou « sql server 2008 » projet ou projet de « sql server 2012 » ou « sql-server-2014 » projet ou projet de « sql azure ». Valeur par défaut est « sql-server-2008 ».  
  
**Exemple de syntaxe :**  
  
```xml  
<create-new-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
  overwrite-if-exists="<true/false>" (optional)  
  
   project-type="<sql-server-2008/sql-server-2005/sql-server-2012/sql-server-2014/sql-azure>"  
/>  
```  
Attribut 'Remplacer-if-exists' est **false** par défaut.  
  
L’attribut « type de projet » est **sql-server-2008** par défaut.  
  
### <a name="open-project"></a>Open-projet  
Cette commande ouvre le projet.

-   `project-folder` Indique le dossier du projet créé. La commande échoue si le dossier spécifié n’existe pas.  {string}  
  
-   `project-name` Indique le nom du projet. La commande échoue si le projet spécifié n’existe pas.  {string}  
  
**Exemple de syntaxe :**  
  
```xml  
<open-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
/>  
```  
> [!NOTE]  
> SSMA pour l’Application de Console SAP ASE prend en charge la compatibilité descendante. Vous pouvez l’utiliser pour ouvrir les projets créés par une version précédente de SSMA.  
  
### <a name="save-project"></a>enregistrer le projet  
Cette commande enregistre le projet de migration.  
  
**Exemple de syntaxe :**  
  
```xml  
<save-project/>  
```  
  
### <a name="close-project"></a>projet-fermer  
Cette commande ferme le projet de migration.  
  
**Exemple de syntaxe :**  
  
```xml  
<close-project   
  if-modified="<save/error/ignore>"   (optional)  
/>  
```  
Attribut « if-modifié » est facultatif, **ignorer** par défaut.  
  
## <a name="database-connection-commands"></a>Commandes de connexion de base de données  
Les commandes de la connexion de base de données permettent de se connecter à la base de données.  
  
> [!NOTE]  
> - Le **Parcourir** fonctionnalité de l’interface utilisateur n’est pas prise en charge dans la console.  
> - Pour plus d’informations sur la « Création de fichiers de Script », consultez [création de fichiers de Script &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-script-files-sybasetosql.md).  
  
### <a name="connect-source-database"></a>se connecter--base de données source  
Cette commande effectue la connexion à la base de données source et charge les métadonnées de haut niveau de la base de données source, mais pas toutes les métadonnées.
  
Si la connexion à la source ne peut pas être établie, une erreur est générée et l’application de console arrête davantage l’exécution.
  
La définition du serveur est récupérée à partir de l’attribut de nom défini pour chaque connexion dans la section serveur de fichier de connexion de serveur ou le fichier de script.  
  
**Exemple de syntaxe :**  
  
```xml  
<connect-source-database  server="<server-unique-name>"/>  
```  
  
### <a name="force-load-sourcetarget-database"></a>force-load-source/cible-base de données  
Cette commande charge les métadonnées de la source, et il est utile pour travailler sur le projet de migration hors connexion.  
  
Si la connexion à la source/cible ne peut pas être établie, une erreur est générée et l’application de console arrête davantage l’exécution.  
  
Cette commande nécessite un ou plusieurs nœuds de la métabase en tant que paramètre de ligne de commande.  
  
**Exemple de syntaxe :**  
  
```xml  
<force-load metabase="<source/target>" >  
  
  <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
  
### <a name="reconnect-source-database"></a>se reconnecter--base de données source  
Cette commande se reconnecte à la base de données source mais ne charge pas toutes les métadonnées contrairement à la commande connect--base de données source.  
  
Si la (connexion avec la source re) ne peut pas être établie, une erreur est générée et l’application de console arrête davantage l’exécution.  
  
**Exemple de syntaxe :**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
  
### <a name="connect-target-database"></a>se connecter--base de données cible  
Cette commande se connecte à la base de données SQL Server cible et charge entièrement les métadonnées de haut niveau de la base de données cible mais pas les métadonnées.  
  
Si la connexion à la cible ne peut pas être établie, une erreur est générée et l’application de console arrête davantage l’exécution.  
  
La définition du serveur est récupérée à partir de l’attribut de nom défini pour chaque connexion dans la section serveur de fichier de connexion de serveur ou le fichier de script.  
  
**Exemple de syntaxe :**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
  
### <a name="reconnect-target-database"></a>se reconnecter--base de données cible  
  
Cette commande se reconnecte à la base de données cible, mais ne charge pas toutes les métadonnées, contrairement à la commande connect--base de données cible.  
  
Si la (connexion à la cible re) ne peut pas être établie, une erreur est générée et l’application de console arrête davantage l’exécution.  
  
**Exemple de syntaxe :**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-commands"></a>Commandes de rapport  
Les commandes de rapport génèrent des rapports sur les performances de diverses activités de la Console SSMA.  
  
### <a name="generate-assessment-report"></a>Générer--rapport d’évaluation  
  
Cette commande génère des rapports d’évaluation sur la base de données source.  
  
Si la connexion de base de données source n’est pas effectuée avant d’exécuter cette commande, une erreur est générée et l’application de console se ferme.  
  
Échec de connexion au serveur de base de données source pendant l’exécution de la commande, entraîne également l’arrêt de l’application de console.  
  
-   `conversion-report-folder:` Spécifie le dossier dans lequel le rapport d’évaluation peut être stocké. (attribut facultatif)  
  
-   `object-name:` Spécifie l’ou les objets pris en compte pour la génération de rapports d’évaluation (noms d’objet individuel prend en charge ou un nom d’objet de groupe).  
  
-   `object-type:` Spécifie le type de l’objet appelé dans l’attribut de nom de l’objet (si la catégorie d’objet est spécifié, le type d’objet est alors « catégorie »).  
  
-   `conversion-report-overwrite:` Spécifie s’il faut remplacer le dossier de rapport d’évaluation s’il existe déjà.  
  
    **Valeur par défaut :** false. (attribut facultatif)  
  
-   `write-summary-report-to:` Spécifie le chemin d’accès auquel le rapport sera généré.  
  
    Si seul le chemin du dossier est mentionné, puis de fichiers par nom **AssessmentReport&lt;n&gt;. XML** est créé. (attribut facultatif)  
  
    La création de rapports a deux sous-catégories supplémentaires :  
  
    -   `report-errors` (= « true/false », valeur par défaut en tant que « false » (attributs facultatifs))  
  
    -   `verbose` (= « true/false », valeur par défaut en tant que « false » (attributs facultatifs))  
  
**Exemple de syntaxe :**  
  
```xml  
<generate-assessment-report  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"  
  
  write-summary-report-to="<file-name/folder-name>"             (optional)  
  
  verbose="<true/false>"                       (optional)  
  
  report-errors="<true/false>"                 (optional)  
  
  assessment-report-folder="<folder-name>"          (optional)  
  
  conversion-report-overwrite="<true/false>"   (optional)  
  
/>  
```  
ou Gestionnaire de configuration  
  
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
Les commandes de Migration convertir le schéma de base de données cible au schéma source et migrent des données vers le serveur cible.  
  
### <a name="convert-schema"></a>convert-schema  
Cette commande effectue la conversion de schéma à partir de la source vers le schéma cible.  
  
Si la connexion de base de données source ou cible n’est pas effectuée avant d’exécuter cette commande, ou la connexion au serveur de base de données source ou cible échoue pendant l’exécution de commande, une erreur est générée et l’application de console se ferme.  
  
-   `conversion-report-folder:` Spécifie le dossier dans lequel le rapport d’évaluation peut être stocké. (attribut facultatif)  
  
-   `object-name:` Spécifie les objets de source pris en compte pour la conversion de schéma (noms d’objet individuel prend en charge ou un nom d’objet de groupe).  
  
-   `object-type:` Spécifie le type de l’objet appelé dans l’attribut de nom de l’objet (si la catégorie d’objet est spécifié, le type d’objet est alors « catégorie »).  
  
-   `conversion-report-overwrite:` Spécifie s’il faut remplacer le dossier de rapport d’évaluation s’il existe déjà.  
  
    **Valeur par défaut :** false. (attribut facultatif)  
  
-   `write-summary-report-to:` Spécifie le chemin d’accès auquel le rapport Résumé sera généré.  
  
    Si seul le chemin du dossier est mentionné, puis de fichiers par nom **SchemaConversionReport&lt;n&gt;. XML** est créé. (attribut facultatif)  
  
    La création de rapports a deux sous-catégories supplémentaires :  
  
    -   `report-errors` (= « true/false », valeur par défaut en tant que « false » (attributs facultatifs))  
  
    -   `verbose` (= « true/false », valeur par défaut en tant que « false » (attributs facultatifs))  
  
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
ou Gestionnaire de configuration  
  
```xml  
<convert-schema  
  
  conversion-report-folder="<folder-name>"         (optional)  
  
  conversion-report-overwrite="<true/false>"> (optional)  
  
  <metabase-object object-name="<object-name>"  
  
    object-type="<object-category>"/>  
  
</convert-schema>  
```  
  
### <a name="migrate-data"></a>migrer des données  
Cette commande migre les données source vers la cible.  
  
-   `object-name:` Spécifie les objets de source pris en compte pour la migration de données (noms d’objet individuel prend en charge ou un nom d’objet de groupe).  
  
-   `object-type:` Spécifie le type de l’objet appelé dans l’attribut de nom de l’objet (si la catégorie d’objet de type d’objet sera « catégorie » n’est spécifié).  
  
-   `write-summary-report-to:` Spécifie le chemin d’accès auquel le rapport sera généré.  
  
    Si seul le chemin du dossier est mentionné, puis de fichiers par nom **DataMigrationReport&lt;n&gt;. XML** est créé. (attribut facultatif)  
  
    La création de rapports a deux sous-catégories supplémentaires :  
  
    -   `report-errors` (= « true/false », valeur par défaut en tant que « false » (attributs facultatifs))  
  
    -   `verbose` (= « true/false », valeur par défaut en tant que « false » (attributs facultatifs))  
  
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
ou Gestionnaire de configuration  
  
```xml  
<migrate-data  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"  
  
  write-summary-report-to="<file-name/folder-name>"  
  
  report-errors="<true/false>" verbose="<true/false>"/>  
```  
  
## <a name="migration-preparation-command"></a>Commande de préparation de migration  
La commande de préparation de la Migration lance le mappage de schéma entre les bases de données source et cible.  
  
> [!NOTE]  
> La sortie de console par défaut définissant pour les commandes de migration est le rapport de sortie « Complète » avec aucun rapport d’erreurs détaillées : Résumé uniquement sur le nœud racine d’arborescence objet source.  
  
### <a name="map-schema"></a>schéma de mappage  
Cette commande fournit le mappage de schéma de la base de données source vers le schéma cible.  
  
-   `source-schema` Spécifie le schéma source à migrer.  
  
-   `sql-server-schema` Spécifie le schéma cible à laquelle le schéma source est migré.  
  
**Exemple de syntaxe :**  
  
```xml  
<map-schema source-schema="<source-schema>"  
  
sql-server-schema="<target-schema>"/>  
```  
  
## <a name="manageability-commands"></a>Commandes de la facilité de gestion  
Les commandes de la facilité de gestion permettent de synchroniser les objets de base de données cible avec la base de données source.  
  
> [!NOTE]  
> La sortie de console par défaut définissant pour les commandes de migration est le rapport de sortie « Complète » avec aucun rapport d’erreurs détaillées : Résumé uniquement sur le nœud racine d’arborescence objet source.  
  
### <a name="synchronize-target"></a>synchroniser la cible  
Cette commande synchronise les objets cibles avec la base de données cible.  
 
Si cette commande est exécutée sur la base de données source, une erreur s’est produite.  
  
Si la connexion de base de données cible n’est pas effectuée avant d’exécuter cette commande, ou la connexion au serveur de base de données cible échoue pendant l’exécution de commande, une erreur est générée et l’application de console se ferme.  
  
-   `object-name:` Spécifie l’ou les objets cible pris en compte pour la synchronisation avec la base de données cible (noms d’objet individuel prend en charge ou un nom d’objet de groupe).  
  
-   `object-type:` Spécifie le type de l’objet appelé dans l’attribut de nom de l’objet (si la catégorie d’objet de type d’objet sera « catégorie » n’est spécifié).  
  
-   `on-error:` Spécifie s’il faut spécifier des erreurs de synchronisation comme des avertissements ou erreurs. Options disponibles pour en cas d’erreur :  
  
    -   Rapport total en tant qu’avertissement  
  
    -   rapport-each-sous-avertissement  
  
    -   Échec-script  
  
-   `report-errors-to:` Spécifie l’emplacement du rapport d’erreurs pour l’opération de synchronisation (attribut facultatif). Si seul le chemin d’accès du dossier est indiqué, puis de fichiers par nom **TargetSynchronizationReport.XML** est créé.  
  
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
ou Gestionnaire de configuration  
  
```xml  
<synchronize-target  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"/>  
```  
ou Gestionnaire de configuration  
  
```xml  
<synchronize-target>  
  
  <metabase-object object-name="<object-name>"/>  
  
  <metabase-object object-name="<object-name>"/>  
  
  <metabase-object object-name="<object-name>"/>  
  
</synchronize-target>  
```  
  
### <a name="refresh-from-database"></a>actualisation de base de données  
Cette commande actualise les objets de la source à partir de la base de données.  
  
Si cette commande est exécutée sur la base de données cible, une erreur est générée.  
  
Cette commande nécessite un ou plusieurs nœuds de la métabase en tant que paramètre de ligne de commande.  
  
-   `object-name:` Spécifie les objets de source pris en compte pour l’actualisation à partir de la base de données source (noms d’objet individuel prend en charge ou un nom d’objet de groupe).  
  
-   `object-type:` Spécifie le type de l’objet spécifié dans l’attribut de nom de l’objet (si la catégorie d’objet de type d’objet sera « catégorie » n’est spécifié).  
  
-   `on-error:` Spécifie s’il faut appeler les erreurs d’actualisation, comme des avertissements ou erreurs. Options disponibles pour en cas d’erreur :  
  
    -   Rapport total en tant qu’avertissement  
  
    -   rapport-each-sous-avertissement  
  
    -   Échec-script  
  
-   `report-errors-to:` Spécifie l’emplacement du rapport d’erreurs pour l’opération d’actualisation (attribut facultatif). Si seul le chemin d’accès du dossier est indiqué, puis de fichiers par nom **SourceDBRefreshReport.XML** est créé.  
  
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
ou Gestionnaire de configuration  
  
```xml  
<refresh-from-database  
  
  object-name="<object-name>"  
  
  object-type="<object-category>" />  
```  
ou Gestionnaire de configuration  
  
```xml  
<refresh-from-database>  
  
  <metabase-object object-name="<object-name>"/>  
  
</refresh-from-database>  
```  
  
## <a name="script-generation-commands"></a>Commandes de génération de script  
Les commandes de génération du Script effectuent des tâches doubles : elles permettent d’enregistrer la sortie dans un fichier de script de console, et ils enregistrent la sortie de T-SQL dans la console ou un fichier basé sur le paramètre que vous spécifiez.  
  
### <a name="save-as-script"></a>Enregistrer en tant que script  
Cette commande est utilisée pour enregistrer les Scripts des objets dans un fichier mentionné lorsque la métabase = cible. Il s’agit d’une alternative à la commande de synchronisation car nous obtenir les scripts et exécuter le même sur la base de données cible.  
  
Cette commande nécessite un ou plusieurs nœuds de la métabase en tant que paramètre de ligne de commande.  
  
-   `object-name:` Spécifie l’ou les objets dont les scripts doivent être enregistrés (noms d’objet individuel prend en charge ou un nom d’objet de groupe).  
  
-   `object-type:` Spécifie le type de l’objet appelé dans l’attribut de nom de l’objet (si la catégorie d’objet est spécifié, le type d’objet est alors « catégorie »).  
  
-   `metabase:` Spécifie s’il s’agit de la source ou cible de la métabase.  
  
-   `destination:` Spécifie le chemin d’accès ou le dossier dans lequel le script doit être enregistré. Si le nom de fichier n’est pas spécifié, un nom de fichier dans le format (valeur d’attribut object_name) .out être fourni.
  
-   `overwrite:` Si la valeur est true, puis il remplace le nom de fichier même si elle existe. Il peut avoir les valeurs (true/false).  
  
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
ou Gestionnaire de configuration  
  
```xml  
<save-as-script  
  
  metabase="<source/target>"  
  
  destination="<file-name/folder-name>"  
  
    <metabase-object object-name="<object-name>"  
  
                     object-type="<object-category>"/>  
  
</save-as-script>  
```  
  
### <a name="convert-sql-statement"></a>instruction CONVERT-sql
Cette commande convertit l’instruction SQL.  
  
-   `context` Spécifie le nom de schéma.  
  
-   `destination` Spécifie si la sortie doit être stockée dans un fichier.  
  
    Si cet attribut n’est pas spécifié, l’instruction T-SQL convertie s’affiche sur la console. (attribut facultatif)  
  
-   `conversion-report-folder` Spécifie le dossier dans lequel le rapport d’évaluation peut être stocké. (attribut facultatif)  
  
-   `conversion-report-overwrite` Spécifie s’il faut remplacer le dossier de rapport d’évaluation s’il existe déjà.  
  
    **Valeur par défaut :** false. (attribut facultatif)  
  
-   `write-converted-sql-to` Spécifie le chemin d’accès de dossier fichier (ou) à laquelle le code T-SQL converti doit être stocké. Quand un chemin d’accès du dossier est spécifié avec la `sql-files` attribut, chaque fichier source a une cible correspondante fichier T-SQL créé sous le dossier spécifié. Quand un chemin d’accès du dossier est spécifié avec la `sql` attribut, le code T-SQL converti est écrit dans un fichier nommé Result.out sous le dossier spécifié.  
  
-   `sql` Spécifie les instructions sql de Sybase à convertir, une ou plusieurs instructions peuvent être séparées par un « ; »  
  
-   `sql-files` Spécifie le chemin d’accès des fichiers de sql qui doit être converti en code T-SQL.  
  
-   `write-summary-report-to` Spécifie le chemin d’accès où le rapport de synthèse est généré. Si seul le chemin du dossier est mentionné, puis de fichiers par nom **ConvertSQLReport.XML** est créé. (attribut facultatif)  
  
    La création de rapport de synthèse a deux sous-catégories supplémentaires, à savoir :  
  
    -   erreurs de rapport (= « true/false », la valeur par défaut en tant que « false » (attributs facultatifs)).  
  
    -   verbose (= « true/false », valeur par défaut en tant que « false » (attributs facultatifs)).  
  
Cette commande nécessite un ou plusieurs nœuds de la métabase en tant que paramètre de ligne de commande.  
  
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
ou Gestionnaire de configuration  
  
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
ou Gestionnaire de configuration  
  
```  
<convert-sql-statement  
  
         context="<database-name>.<schema-name>"  
  
         conversion-report-folder="<folder-name>"  
  
         conversion-report-overwrite="<true/false>"  
  
         sql-files="<folder-name>\*.sql"  
  
/>  
```  
  
## <a name="next-steps"></a>Étapes suivantes  
Pour plus d’informations sur les options de ligne de commande, consultez [des options de ligne de commande dans la Console SSMA (AccessToSQL)](../access/command-line-options-in-ssma-console-accesstosql.md).  
  
Pour plus d’informations sur un exemple de fichier de script de console, consultez [fonctionne avec les exemples de fichiers de Script de Console &#40;SybaseToSQL&#41;](../../ssma/sybase/working-with-the-sample-console-script-files-sybasetosql.md)  
  
L’étape suivante varie selon les spécifications de votre projet :  
  
-   Pour spécifier un mot de passe ou d’exportation / importation des mots de passe, consultez [la gestion des mots de passe &#40;SybaseToSQL&#41;](../../ssma/sybase/managing-passwords-sybasetosql.md).  
  
-   Pour générer des rapports, consultez [génération de rapports &#40;SybaseToSQL&#41;](../../ssma/sybase/generating-reports-sybasetosql.md).  
  
-   Pour résoudre les problèmes dans la console, consultez [dépannage &#40;SybaseToSQL&#41;](../../ssma/sybase/troubleshooting-sybasetosql.md).  
  
