---
title: Exécution de la Console SSMA (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: aa1bf665-8dc0-4259-b36f-46ae67197a43
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: d1dbbb57527fc2d362837e0340f35a241d764b75
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52408316"
---
# <a name="executing-the-ssma-console-accesstosql"></a>Exécution de la Console SSMA (AccessToSQL)
Microsoft vous offre un ensemble complet de commandes de fichier de script et les options de ligne de commande pour exécuter et contrôler les activités SSMA. Les sections suivantes détaillent les mêmes.  
  
## <a name="project--script-file-commands"></a>Commandes de fichier de Script de projet  
Les commandes de projet gèrent la création de projets, ouvrir, enregistrer et quitter des projets.  
  
**Commande**  
  
Créer-nouveau projet : Crée un nouveau projet SSMA.  
  
**Script**  
  
-   `project-folder` Indique le dossier du projet créé.  
  
-   `project-name` Indique le nom du projet. {string}  
  
-   `overwrite-if-exists`Attribut facultatif indique si un projet existant doit être remplacé. {valeur booléenne}  
  
-   `project-type` est un attribut facultatif.  Les options suivantes sont disponibles pour le type de projet :  
  
    -   SQL-server-2005  
  
    -   SQL-server-2008  
  
    -   SQL-server-2012  
  
    -   SQL-server-2014  
  
    -   SQL-server-2016  
  
    -   SQL azure  
  
    Valeur par défaut est « sql server 2008 ».  
  
**Exemple :**  
  
```xml  
<create-new-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
  overwrite-if-exists="<true/false>"  
  
  project-type="<sql-server-2008 | sql-server-2005 | sql-server-2012 | sql-server-2014 | sql-azure>"  
  
/>  
```  
Attribut 'Remplacer-if-exists' est **false** par défaut.  
  
L’attribut « type de projet » est **sql-server-2008** par défaut.  
  
**Commande**  
  
Open-projet : Ouvre un projet existant.  
  
**Script**  
  
-   `project-folder` Indique le dossier du projet créé. La commande échoue si le dossier spécifié n’existe pas.  {string}  
  
-   `project-name` Indique le nom du projet. La commande échoue si le projet spécifié n’existe pas.  {string}  
  
**Exemple de syntaxe :**  
  
```xml  
<open-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
/>  
```  
**Remarque :** Application de Console SSMA pour Access prend en charge la compatibilité descendante. Vous ne pourrez pas ouvrir les projets créés par une version précédente de SSMA.  
  
**Commande**  
  
projet de l’enregistrement : Enregistre le projet de migration.  
  
**Script**  
  
**Exemple de syntaxe :**  
  
```xml  
<save-project/>  
```  
**Commande**  
  
projet de fermeture : Ferme le projet de migration.  
  
**Script**  
  
**Exemple de syntaxe :**  
  
```xml  
<close-project  
  
  if-modified="<save/error/ignore>"   (optional)  
  
/>  
```  
Attribut « if-modifié » est facultatif, **ignorer** par défaut.  
  
## <a name="database-connection-script-file-commands"></a>Commandes de fichier de Script de connexion de base de données  
Les commandes de la connexion de base de données permettent de se connecter à la base de données.  
  
Le **Parcourir** fonctionnalité de l’interface utilisateur n’est pas prise en charge dans la console.  
  
Le **l’authentification windows** et **port** paramètres ne sont pas applicables lors de la connexion à SQL Azure.  
  
Pour plus d’informations sur la « Création de fichiers de Script », consultez [création de fichiers de Script &#40;AccessToSQL&#41;](../../ssma/access/creating-script-files-accesstosql.md).  
  
**Commande**  
  
se connecter--base de données source  
  
-   Effectue la connexion à la base de données source et charge les métadonnées de niveau élevée de la base de données source mais pas toutes les métadonnées.  
  
-   Si la connexion à la source ne peut pas être établie, une erreur est générée et l’application de console arrête davantage l’exécution  
  
**Script**  
  
Définition de serveur est récupérée à partir de l’attribut de nom défini pour chaque connexion dans la section serveur de fichier de connexion de serveur ou le fichier de script.  
  
**Exemple de syntaxe :**  
  
```xml  
<connect-source-database  server="<server-unique-name>"/>  
```  
**Commande**  
  
accès-base de données charge : Permet de charger des fichiers de base de données access  
  
**Script**  
  
**Exemple de syntaxe :**  
  
```xml  
<load-access-database  database-file="<Access-database>"/>  
```  
ou Gestionnaire de configuration  
  
```xml  
<load-access-database>  
  
  <access-database database-file="<Access-database1>"/>  
  
  <access-database database-file="<Access-database2>"/>  
  
</load-access-database>  
```  
**Commande**  
  
force-load-source/cible-base de données  
  
-   Charge les métadonnées de la source.  
  
-   Utile pour travailler sur le projet de migration hors connexion.  
  
-   Si la connexion à la source/cible ne peut pas être établie, une erreur est générée et l’application de console arrête davantage l’exécution  
  
**Script**  
  
Nécessite un ou plusieurs nœuds de la métabase en tant que paramètre de ligne de commande.  
  
**Exemple de syntaxe :**  
  
```xml  
<force-load  
  
  object-name="<object-name>"  
  
  metabase="<source/target>"/>  
```  
ou Gestionnaire de configuration  
  
```xml  
<force-load>  
  
  <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
**Commande**  
  
se reconnecter--base de données source  
  
-   Se reconnecte à la base de données source mais ne se charge pas toutes les métadonnées contrairement à la commande connect--base de données source.  
  
-   Si la (connexion avec la source re) ne peut pas être établie, une erreur est générée et l’application de console arrête davantage l’exécution.  
  
**Script**  
  
**Exemple de syntaxe :**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
**Commande**  
  
se connecter--base de données cible  
  
-   Se connecte à la base de données SQL Server ou SQL Azure cible et charge entièrement les métadonnées de niveau élevée de la base de données cible mais pas les métadonnées.  
  
-   Si la connexion à la cible ne peut pas être établie, une erreur est générée et l’application de console arrête davantage l’exécution.  
  
**Script**  
  
Définition de serveur est récupérée à partir de l’attribut de nom défini pour chaque connexion dans la section serveur de fichier de connexion de serveur ou le fichier de script  
  
**Exemple de syntaxe :**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
**Commande**  
  
se reconnecter--base de données cible  
  
-   Se reconnecte à la base de données cible, mais ne se charge pas toutes les métadonnées, contrairement à la commande connect--base de données cible.  
  
-   Si la (connexion à la cible re) ne peut pas être établie, une erreur est générée et l’application de console arrête davantage l’exécution.  
  
**Script**  
  
**Exemple de syntaxe :**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-script-file-commands"></a>Commandes de fichier de Script de rapport  
Les commandes de rapport génèrent des rapports sur les performances de diverses activités de la Console SSMA.  
  
**Commande**  
  
Générer--rapport d’évaluation  
  
-   Génère des rapports d’évaluation sur la base de données source.  
  
-   Si la connexion de base de données source n’est pas effectuée avant d’exécuter cette commande, une erreur est générée et l’application de console se ferme.  
  
-   Échec de connexion au serveur de base de données source pendant l’exécution de la commande, entraîne également l’arrêt de l’application de console.  
  
**Script**  
  
-   `assessment-report-folder:` Spécifie le dossier dans lequel le rapport d’évaluation peut être stockées. (attribut facultatif)  
  
-   `object-name:` Spécifie l’ou les objets pris en compte pour la génération de rapports d’évaluation (il peut avoir les noms d’objets individuels ou un nom d’objet de groupe).  
  
-   `object-type:` Spécifie le type de l’objet spécifié dans l’attribut de nom de l’objet (si la catégorie d’objet de type d’objet sera « catégorie » n’est spécifié).  
  
-   `assessment-report-overwrite:` Spécifie s’il faut remplacer le dossier de rapport d’évaluation s’il existe déjà.  
  
    **Valeur par défaut :** false. (attribut facultatif)  
  
-   `write-summary-report-to:` Spécifie le chemin d’accès où le rapport sera généré.  
  
    Si seul le chemin du dossier est mentionné, puis de fichiers par nom **AssessmentReport&lt;n&gt;. XML** est créé. (attribut facultatif)  
  
    La création de rapports a deux sous-catégories supplémentaires :  
  
    -   `report-errors` (= « true/false », valeur par défaut en tant que « false » (attributs facultatifs))  
  
    -   `verbose` (= « true/false », valeur par défaut en tant que « false » (attributs facultatifs))  
  
**Exemple de syntaxe :**  
  
```xml  
<generate-assessment-report  
  
  object-name="ssma.Procedures"  
  
  object-type="category"  
  
  write-summary-report-to="<file>"             (optional)  
  
  verbose="<true/false>"                       (optional)  
  
  report-errors="<true/false>"                 (optional)  
  
  conversion-report-folder="<folder>"          (optional)  
  
  conversion-report-overwrite="<true/false>"   (optional)  
  
/>  
```  
ou Gestionnaire de configuration  
  
```xml  
<generate-assessment-report  
  
  conversion-report-folder="<folder>"            (optional)  
  
  conversion-report-overwrite="<true/false>"     (optional)  
  
>  
    <metabase-object object-name="ssma.Procedures"  
  
        object-type="category"/>  
  
</generate-assessment-report>  
```  
  
## <a name="migration-script-file-commands"></a>Commandes de fichier de Script de migration  
Les commandes de Migration convertir le schéma de base de données cible au schéma source et migre les données vers le serveur cible.  
  
La sortie de console par défaut définissant pour les commandes de migration est le rapport de sortie « Complète » avec aucun rapport d’erreurs détaillées : Résumé uniquement sur le nœud racine d’arborescence objet source.  
  
**Commande**  
  
convert-schema  
  
-   Effectue une conversion de schéma à partir de la source vers le schéma cible.  
  
-   Si la connexion de base de données source ou cible n’est pas effectuée avant d’exécuter cette commande, ou la connexion au serveur de base de données source ou cible échoue pendant l’exécution de commande, une erreur est générée et l’application de console se ferme.  
  
**Script**  
  
-   `conversion-report-folder:` Spécifie le dossier où le rapport d’évaluation peut être stocké. (attribut facultatif)  
  
-   `object-name:` Spécifie les objets de source pris en compte pour la conversion de schéma (il peut avoir les noms d’objets individuels ou un nom d’objet de groupe).  
  
-   `object-type:` Spécifie le type de l’objet spécifié dans l’attribut de nom de l’objet (si la catégorie d’objet de type d’objet sera « catégorie » n’est spécifié).  
  
-   `conversion-report-overwrite:` Spécifie s’il faut remplacer le dossier de rapport d’évaluation s’il existe déjà.  
  
    **Valeur par défaut :** false. (attribut facultatif)  
  
-   `write-summary-report-to:` Spécifie le chemin d’accès où le rapport sera généré.  
  
    Si seul le chemin du dossier est mentionné, puis de fichiers par nom **SchemaConversionReport&lt;n&gt;. XML** est créé. (attribut facultatif)  
  
    La création de rapports a deux sous-catégories supplémentaires :  
  
    -   `report-errors` (= « true/false », valeur par défaut en tant que « false » (attributs facultatifs))  
  
    -   `verbose` (= « true/false », valeur par défaut en tant que « false » (attributs facultatifs))  
  
**Exemple de syntaxe :**  
  
```xml  
<convert-schema  
  
  object-name="ssma.Procedures"  
  
  object-type="category"  
  write-summary-report-to="<filepath/folder>"     (optional)  
  
  verbose="<true/false>"                          (optional)  
  
  report-errors="<true/false>"                    (optional)  
  
  conversion-report-folder="<folder>"             (optional)  
  
  conversion-report-overwrite="<true/false>"      (optional)  
  
/>  
```  
ou Gestionnaire de configuration  
  
```xml  
<convert-schema  
  
  conversion-report-folder="<folder>"         (optional)  
  
  conversion-report-overwrite="<true/false>"  (optional)  
  
  <metabase-object object-name="ssma.Procedures"  
  
    object-type="category"/>  
  
</convert-schema>  
```  
**Commande**  
  
migrer des données  
  
1.  Migre les données source vers la cible.  
  
**Script**  
  
-   `object-name:` Spécifie les objets de source pris en compte pour la migration de données (il peut avoir les noms d’objets individuels ou un nom d’objet de groupe).  
  
-   `object-type:` Spécifie le type de l’objet spécifié dans l’attribut de nom de l’objet (si la catégorie d’objet de type d’objet sera « catégorie » n’est spécifié).  
  
-   `write-summary-report-to:` Spécifie le chemin d’accès où le rapport sera généré.  
  
    Si seul le chemin du dossier est mentionné, puis de fichiers par nom **DataMigrationReport&lt;n&gt;. XML** est créé. (attribut facultatif)  
  
    La création de rapports a deux sous-catégories supplémentaires :  
  
    -   `report-errors` (= « true/false », valeur par défaut en tant que « false » (attributs facultatifs))  
  
    -   `verbose` (= « true/false », valeur par défaut en tant que « false » (attributs facultatifs))  
  
**Exemple de syntaxe :**  
  
```xml  
<migrate-data  
  
  write-summary-report-to="<filepath/folder>"  
  
  report-errors="true" verbose="true">  
  
    <metabase-object object-name="ssma.TT1"/>  
  
    <metabase-object object-name="ssma.TT2"/>  
  
    <metabase-object object-name="ssma.TT3"/>  
  
    <data-migration-connection  
  
      source-use-last-used="true"/source-server="<server-unique-name>"  
  
      target-use-last-used="true"/target-server="<server-unique-name>"/>  
  
</migrate-data>  
```  
ou Gestionnaire de configuration  
  
```xml  
<migrate-data  
  
  object-name="ssma.Tables"  
  
  object-type="category"  
  
  write-summary-report-to="<filepath/folder>"  
  
  report-errors="true" verbose="true"/>  
```  
**Commande**  
  
lien-tables : Cette commande lie la table source (accès) à la table cible.  
  
**Script**  
  
**Exemple de syntaxe :**  
  
```xml  
<link-tables>  
  
  <metabase-object object-name="AccessDatabase.table1" object-type="Tables"/>  
  
  <metabase-object object-name="AccessDatabase.table2" object-type="Tables"/>  
  
</link-tables>  
```  
ou Gestionnaire de configuration  
  
```xml  
<link-tables>  
  
  <metabase-object object-name="AccessDatabase.Tables" object-type="category"/>  
  
</link-tables>  
```  
**Commande**  
  
Dissocier-tables : Cette commande supprime la table source (accès) à partir de la table cible.  
  
**Script**  
  
**Exemples de syntaxe :**  
  
```xml  
<unlink-tables>  
  
  <metabase-object object-name="AccessDatabase.table1" object-type="Tables"/>  
  
  <metabase-object object-name="AccessDatabase.table2" object-type="Tables"/>  
  
</unlink-tables>  
```  
ou Gestionnaire de configuration  
  
```xml  
<unlink-tables>  
  
  <metabase-object object-name="AccessDatabase.Tables" object-type="category"/>  
  
</unlink-tables>  
```  
  
## <a name="migration-preparation-script-file-commands"></a>Commandes de fichier de Script de préparation migration  
La commande de préparation de la Migration lance le mappage de schéma entre les bases de données source et cible.  
  
**Commande**  
  
schéma du mappage : Mappage de schéma de base de données source vers le schéma cible.  
  
**Script**  
  
-   `source-schema` Spécifie le schéma source que nous avons l’intention de migrer.  
  
-   `sql-server-schema` Spécifie le schéma cible que nous voulons être migrés.  
  
**Exemple de syntaxe :**  
  
```xml  
<map-schema source-schema="source-schema"  
  
            sql-server-schema="target-schema"/>  
```  
  
## <a name="manageability-commands"></a>Commandes de la facilité de gestion  
Les commandes de la facilité de gestion permettent de synchroniser les objets de base de données cible avec la base de données source.  
  
La sortie de console par défaut définissant pour les commandes de migration est le rapport de sortie « Complète » avec aucun rapport d’erreurs détaillées : Résumé uniquement sur le nœud racine d’arborescence objet source.  
  
**Commande**  
  
synchroniser la cible  
  
1.  Synchronise les objets cibles avec la base de données cible.  
  
2.  Si cette commande est exécutée sur la base de données source, une erreur s’est produite.  
  
3.  Si la connexion de base de données cible n’est pas effectuée avant d’exécuter cette commande, ou la connexion au serveur de base de données cible échoue pendant l’exécution de commande, une erreur est générée et l’application de console se ferme.  
  
**Script**  
  
1.  `object-name:` Spécifie l’ou les objets cible pris en compte pour la synchronisation avec la base de données cible (il peut avoir les noms d’objets individuels ou un nom d’objet de groupe).  
  
2.  `object-type:` Spécifie le type de l’objet spécifié dans l’attribut de nom de l’objet (si la catégorie d’objet de type d’objet sera « catégorie » n’est spécifié).  
  
3.  `on-error:` Spécifie s’il faut spécifier des erreurs de synchronisation comme des avertissements ou erreurs. Options disponibles pour en cas d’erreur :  
  
    -   Rapport total en tant qu’avertissement  
  
    -   rapport-each-sous-avertissement  
  
    -   Échec-script  
  
4.  `report-errors-to:` Spécifie l’emplacement du rapport d’erreurs pour l’opération de synchronisation (attribut facultatif) si seul le chemin d’accès du dossier est indiqué, puis de fichiers par nom **TargetSynchronizationReport.XML** est créé.  
  
**Exemple de syntaxe :**  
  
```xml  
<synchronize-target  
  
  object-name="ots_triggers.dbo"  
  
  on-error="<report-total-as-warning|  
  
             report-each-as-warning|  
  
             fail-script>"              (optional)  
  
  report-errors-to="<file-name>"        (optional)  
  
/>  
```  
ou Gestionnaire de configuration  
  
```xml  
<synchronize-target  
  
  object-name="ssma.dbo.Procedures"  
  
  object-type="category"/>  
```  
ou Gestionnaire de configuration  
  
```xml  
<synchronize-target>  
  
  <metabase-object object-name="ssma.dbo.TT1"/>  
  
  <metabase-object object-name="ssma.dbo.TT2"/>  
  
  <metabase-object object-name="ssma.dbo.TT3"/>  
  
</synchronize-target>  
```  
**Commande**  
  
actualisation de base de données  
  
-   Actualise les objets de la source à partir de la base de données.  
  
-   Si cette commande est exécutée sur la base de données cible, une erreur est générée.  
  
**Script**  
  
Nécessite un ou plusieurs nœuds de la métabase en tant que paramètre de ligne de commande.  
  
1.  `object-name:` Spécifie les objets de source pris en compte pour l’actualisation à partir de la base de données source (il peut avoir les noms d’objets individuels ou un nom d’objet de groupe).  
  
2.  `object-type:` Spécifie le type de l’objet spécifié dans l’attribut de nom de l’objet (si la catégorie d’objet de type d’objet sera « catégorie » n’est spécifié).  
  
3.  `on-error:` Spécifie s’il faut spécifier des erreurs d’actualisation comme des avertissements ou erreurs. Options disponibles pour en cas d’erreur :  
  
    -   Rapport total en tant qu’avertissement  
  
    -   rapport-each-sous-avertissement  
  
    -   Échec-script  
  
4.  `report-errors-to:` Spécifie l’emplacement du rapport d’erreurs pour l’opération d’actualisation (attribut facultatif) si seul le chemin d’accès du dossier est indiqué, puis de fichiers par nom **SourceDBRefreshReport.XML** est créé.  
  
**Exemple de syntaxe :**  
  
```xml  
<refresh-from-database  
  
  object-name="ssma.TT1"  
  
  on-error="<report-total-as-warning|  
  
             report-each-as-warning|  
  
             fail-script>"              (optional)  
  
  report-errors-to="<file-name>"        (optional)  
  
/>  
```  
ou Gestionnaire de configuration  
  
```xml  
<refresh-from-database  
  
  object-name="ssma.Procedures"  
  
  object-type="category"/>  
```  
ou Gestionnaire de configuration  
  
```xml  
<refresh-from-database>  
  
  <metabase-object object-name="ssma.TT_1"/>  
  
</refresh-from-database>  
```  
  
## <a name="script-generation-script-file-commands"></a>Commandes de fichier de Script de génération script  
La génération du Script de commandes vous permettent d’enregistrer la sortie de console dans un fichier de script.  
  
**Commande**  
  
Enregistrer en tant que script  
  
Utilisé pour enregistrer les Scripts des objets dans un fichier mentionné lorsque la métabase = cible, il s’agit d’une alternative à la commande de synchronisation là où nous obtenir les scripts dans et exécutez le même sur la base de données cible.  
  
**Script**  
  
Nécessite un ou plusieurs nœuds de la métabase en tant que paramètre de ligne de commande.  
  
-   `object-name:` Spécifie l’ou les objets dont les scripts doivent être enregistrés. (Il peut avoir les noms d’objets individuels ou un nom d’objet de groupe)  
  
-   `object-type:` Spécifie le type de l’objet spécifié dans l’attribut de nom de l’objet (si la catégorie d’objet de type d’objet sera « catégorie » n’est spécifié).  
  
-   `metabase:` Spécifie s’il s’agit de la source ou cible de la métabase.  
  
-   `destination:` Spécifie le chemin d’accès ou le dossier dans lequel le script doit être enregistré, si le nom de fichier n’est indiqué ensuite un nom de fichier dans le format (valeur d’attribut object_name) .out  
  
-   `overwrite:` Si true elle remplace si le même nom de fichier existe. Il peut avoir les valeurs (true/false).  
  
**Exemple de syntaxe :**  
  
```xml  
<save-as-script  
  
  metabase="<source/target>"  
  
  object-name="ssma.dbo.Procedures"  
  
  object-type="category"  
  
  destination="<file/folder>"  
  
  overwrite="<true/false>"             (optional)  
  
/>  
```  
ou Gestionnaire de configuration  
  
```xml  
<save-as-script  
  
  metabase="<source/target>"  
  
  destination="<file/folder>"  
  
    <metabase-object object-name="ssma.dbo.Procedures"  
  
                     object-type="category"/>  
  
</save-as-script>  
```  
  
## <a name="next-step"></a>Étape suivante  
Pour plus d’informations sur les options de ligne de commande, consultez [les Options de ligne de commande dans la Console SSMA &#40;AccessToSQL&#41; ](../../ssma/access/command-line-options-in-ssma-console-accesstosql.md) .  
  
Pour plus d’informations sur les exemples de fichiers de script console, consultez [le FilesExecuting de Script de Console exemple utilisation de la Console SSMA &#40;AccessToSQL&#41;](../../ssma/access/working-sample-console-script-filesexecuting-ssma-console-accesstosql.md)  
  
L’étape suivante varie selon les spécifications de votre projet :  
  
-   Pour spécifier un mot de passe ou d’exportation / importation des mots de passe, consultez [la gestion des mots de passe &#40;AccessToSQL&#41;](../../ssma/access/managing-passwords-accesstosql.md).  
  
-   Pour générer des rapports, consultez [génération de rapports &#40;AccessToSQL&#41;](../../ssma/access/generating-reports-accesstosql.md).  
  
-   Pour résoudre les problèmes dans la console, consultez [dépannage &#40;AccessToSQL&#41;](../../ssma/access/troubleshooting-accesstosql.md).  
  
