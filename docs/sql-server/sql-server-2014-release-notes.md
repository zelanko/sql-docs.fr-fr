---
title: "Notes de publication de SQL Server 2014 | Microsoft Docs"
ms.custom: 
ms.date: 01/31/2017
ms.prod: sql-server-2014
ms.technology: server-general
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf4c4922-80b3-4be3-bf71-228247f97004
caps.latest.revision: 100
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: cd1366409f9fb0af271b26fad3b8b911f99acc06
ms.openlocfilehash: d6d229c14056f9157bd219ba6cbb7590eb14a7b7
ms.contentlocale: fr-fr
ms.lasthandoff: 09/08/2017

---
# <a name="sql-server-2014-release-notes"></a>Notes de publication de SQL Server 2014
Ce document Notes de publication décrit les problèmes connus que vous devez examiner avant d'installer ou de dépanner [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
## <a name="top"></a>Sommaire  
[1.0 Avant l’installation](#BeforeInstall)  
  
[2.0 Documentation du produit](#ProdDoc)  
  
[3.0 Moteur de base de données](#DBEngine)  
  
[4.0 Reporting Services](#SSRS)  
  
[5.0 SQL Server 2014 sur des machines virtuelles Microsoft Azure](#AzureVM)  
  
[6.0 Analysis Services](#SSAS)  
  
[7.0 Data Quality Services](#DQS)  
  
[8.0 Conseiller de mise à niveau](#UA)  
  
## <a name="BeforeInstall"></a>1.0 Avant l’installation  
  
### <a name="11-limitations-and-restrictions-in-sql-server-2014-rtm"></a>1.1 Limitations et restrictions dans SQL Server 2014 RTM  
  
#### <a name="111-general-limitations-and-restrictions"></a>1.1.1 Limitations et restrictions générales  
  
1.  La mise à niveau de SQL Server 2014 CTP 1 vers SQL Server 2014 RTM N'est PAS prise en charge.  
  
2.  L'installation de SQL Server 2014 CTP 1 côte à côte avec SQL Server 2014 RTM N'est PAS prise en charge.  
  
3.  L'attachement ou la restauration d'une base de données SQL Server 2014 CTP 1 vers SQL Server 2014 RTM N'est PAS prise en charge.  
  
**Solution de contournement :** aucune.  
  
#### <a name="12-considerations-for-upgrading-sql-server-2014-ctp-2-to-sql-server-2014-rtm-and-downgrading-from-sql-server-2014-rtm-to-sql-server-2014-ctp-2"></a>1.2 Éléments à prendre en considération pour la mise à niveau de SQL Server 2014 CTP 2 vers SQL Server 2014 RTM et pour la migration de SQL Server 2014 RTM vers SQL Server 2014 CTP 2  
  
#### <a name="121-upgrading-from-sql-server-2014-ctp-2-to-sql-server-rtm-is-fully-supported"></a>1.2.1 La mise à niveau de SQL Server 2014 CTP 2 vers SQL Server RTM est totalement prise en charge.  
Plus précisément, vous pouvez :  
  
1.  Attacher une base de données SQL Server 2014 CTP 2 à une instance de SQL Server 2014 RTM.  
  
2.  Restaurer une sauvegarde de base de données prise sur SQL Server 2014 CTP 2 sur une instance de SQL Server 2014 RTM.  
  
3.  Mettre à niveau sur place vers SQL Server 2014 RTM.  
  
4.  Mettre à niveau de façon propagée vers SQL Server 2014 RTM. Vous devez passer en mode de basculement manuel avant d'initialiser la mise à niveau propagée. Reportez-vous à [Mise à niveau et mise à jour des serveurs d'un groupe de disponibilité avec un temps mort et une perte de données minimaux](http://msdn.microsoft.com/library/dn178483.aspx) pour plus de détails.  
  
5.  Les données collectées par les jeux d'éléments de collecte des performances des transactions installés dans SQL Server 2014 CTP 2 ne peuvent pas être affichées par SQL Server Management Studio dans SQL Server 2014 RTM, et vice versa. Utilisez SQL Server Management Studio dans SQL Server 2014 CTP 2 pour afficher les données collectées par le jeu d'éléments de collecte installé dans SQL Server 2014 CTP 2, et utilisez SQL Server Management Studio dans SQL Server 2014 RTM pour afficher les données collectées par le jeu d'éléments de collecte installé dans SQL Server 2014 RTM.  
  
### <a name="122-downgrading-from-sql-server-2014-rtm-to-sql-server-2014-ctp-2"></a>1.2.2 Migration de SQL Server 2014 RTM vers SQL Server 2014 CTP 2  
Cela n'est pas pris en charge.  
  
**Solution de contournement :** il n'existe pas de solution pour la migration vers une version antérieure. Nous vous recommandons de sauvegarder la base de données avant la mise à niveau vers SQL Server 2014 RTM.  
  
![Icône de flèche utilisée avec le lien Retour au début](../sql-server/media/uparrow16x16.gif "Icône de flèche utilisée avec le lien Retour au début")[Début](#top)  
  
## <a name="13-incorrect-version-of-streaminsight-client-on-sql-server-2014-mediaisocab"></a>1.3 Version incorrecte du client StreamInsight sur média/ISO/CAB SQL Server 2014  
La version incorrecte de StreamInsight.msi et StreamInsightClient.msi se trouve dans le chemin suivant du média SQL Server/ISO/CAB (StreamInsight\\\<Architecture\>\\\<ID de langue\>).  
  
**Solution de contournement :** téléchargez et installez la version correcte à partir de la [page de téléchargement de SQL Server 2014 Feature Pack](http://go.microsoft.com/fwlink/?LinkID=306709).  
  
## <a name="ProdDoc"></a>2.0 Documentation du produit  
  
### <a name="21-report-builder-content-is-not-available-in-some-languages"></a>2.1 Le contenu du Générateur de rapports n'est pas disponible dans toutes les langues  
**Problème** : le contenu du Générateur de rapports est disponible uniquement dans les langues suivantes :  
  
-   Grec (el-GR)  
  
-   Norvégien (Bokmal) (nb-NO)  
  
-   Finnois (fi Fi)  
  
-   Danois (da-DK)  
  
Dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], ce contenu était disponible dans un fichier CHM fourni avec le produit et disponible dans ces langues. Les fichiers CHM ne sont plus fournis avec le produit et le contenu du Générateur de rapports est uniquement disponible sur MSDN. MSDN ne prend pas en charge ces langues. Le Générateur de rapports a également été supprimé de TechNet, et n'est donc plus disponible dans les langues prises en charge.  
  
**Solution de contournement :** aucune.  
  
### <a name="22-powerpivot-content-is-not-available-in-some-languages"></a>2.2 Le contenu PowerPivot n'est pas disponible dans toutes les langues  
**Problème** : le contenu Power Pivot n'est pas disponible dans les langues suivantes :  
  
-   Grec (el-GR)  
  
-   Norvégien (Bokmal) (nb-NO)  
  
-   Finnois (fi Fi)  
  
-   Danois (da-DK)  
  
-   Tchèque (cs-CZ)  
  
-   Hongrois (hu-HU)  
  
-   Néerlandais (Pays-Bas) (nl-NL)  
  
-   Polonais (pl-PL)  
  
-   Suédois (sv-SE)  
  
-   Turc (tr-TR)  
  
-   Portugais (Portugal) (pt-PT)  
  
Dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], ce contenu était disponible sur TechNet et dans ces langues. Ce contenu a été supprimé de TechNet, et n'est plus disponible dans les langues prises en charge.  
  
**Solution de contournement :** aucune.  
  
![Icône de flèche utilisée avec le lien Retour au début](../sql-server/media/uparrow16x16.gif "Icône de flèche utilisée avec le lien Retour au début")[Début](#top)  
  
## <a name="DBEngine"></a>3.0 Moteur de base de données  
  
### <a name="31-changes-made-for-standard-edition-in-sql-server-2014-rtm"></a>3.1 Modifications apportées à l'édition Standard dans SQL Server 2014 RTM  
L'édition SQL Server 2014 Standard comprend les modifications suivantes :  
  
-   La fonctionnalité d'extension du pool de mémoires tampons autorise l'utilisation d'une taille maximale allant jusqu'à 4 fois la mémoire configurée.  
  
-   La mémoire maximale est passée de 64 Go à 128 Go.  
  
### <a name="32-in-memory-oltp-issues"></a>3.2 Problèmes liés à OLTP en mémoire  
  
#### <a name="321-memory-optimization-advisor-flags-default-constraints-as-incompatible"></a>3.2.1 Le Conseiller d'optimisation de la mémoire signale les contraintes par défaut comme incompatibles  
**Problème :** le Conseiller d'optimisation de la mémoire dans SQL Server Management Studio signale toutes les contraintes par défaut comme étant incompatibles. Certaines contraintes par défaut ne sont pas prises en charge dans une table mémoire optimisée ; le Conseiller ne fait pas de distinction entre les types de contraintes par défaut prises en charge et non prises en charge. Les contraintes par défaut prises en charge incluent notamment toutes les constantes, les expressions et les fonctions intégrées prises en charge dans les procédures stockées compilées en mode natif. Pour afficher la liste des fonctions prises en charge dans les procédures stockées compilées en mode natif, consultez [Constructions prises en charge dans les procédures stockées compilées en mode natif](http://msdn.microsoft.com/library/dn452279(v=sql.120).aspx).  
  
**Solution de contournement :** si vous voulez utiliser le Conseiller pour identifier les bloqueurs, ignorez les contraintes par défaut compatibles. Pour utiliser le Conseiller d'optimisation de la mémoire pour migrer des tables ayant des contraintes par défaut compatibles, mais aucun autre bloqueur, suivez ces étapes :  
  
1.  Supprimez les contraintes par défaut de la définition de table.  
  
2.  Utilisez le Conseiller pour obtenir un script de migration sur la table.  
  
3.  Rajoutez les contraintes par défaut dans le script de migration.  
  
4.  Exécutez le script de migration.  
  
#### <a name="322-informational-message-file-access-denied-incorrectly-reported-as-an-error-in-the-sql-server-2014-error-log"></a>3.2.2 Le message d'information « accès au fichier refusé » est signalé comme erreur dans le journal des erreurs SQL Server 2014  
**Problème :** lors du redémarrage d'un serveur qui a des bases de données contenant des tables mémoire optimisées, vous pouvez voir le type de message d'erreur suivant dans le journal des erreurs SQL Server 2014 :  
  
```  
[ERROR]Unable to delete file C:\Program Files\Microsoft SQL   
Server\....old.dll. This error may be due to a previous failure to unload   
memory-optimized table DLLs.  
```  
  
Ce message est en fait fourni uniquement à titre d'information. Aucune action n'est requise de la part de l'utilisateur.  
  
**Solution de contournement :** aucune. Ce message est fourni à titre d'information.  
  
#### <a name="323-missing-index-details-incorrectly-report-included-columns-for-memory-optimized-table"></a>3.2.3 Les détails d'index absent signalent incorrectement des colonnes incluses pour la table mémoire optimisée  
**Problème :** si SQL Server 2014 détecte un index absent pour une requête sur une table mémoire optimisée, il signale un index absent dans SHOWPLAN_XML, ainsi que dans les vues de gestion dynamique de l'index absent, par exemple sys.dm_db_missing_index_details. Dans certains cas, les détails de l'index absent contiendront des colonnes incluses. Bien que toutes les colonnes soient implicitement incluses avec tous les index des tables mémoire optimisées, il n'est pas possible de spécifier explicitement les colonnes incluses avec des index mémoire optimisés.  
  
**Solution de contournement :** ne spécifiez pas la clause INCLUDE pour des index de tables mémoire optimisées.  
  
#### <a name="324-missing-index-details-omit-missing-indexes-if-a-hash-index-exists-but-is-not-suitable-for-the-query"></a>3.2.4 Les détails d'index absent omettent les index absents si un index hach existe mais n'est pas approprié pour la requête  
**Problème :** si un index HASH sur les colonnes d'une table mémoire optimisée est référencé dans une requête, mais que l'index ne peut pas être utilisé pour la requête, SQL Server 2014 ne signale pas toujours d'index absent dans SHOWPLAN_XML et dans la vue de gestion dynamique sys.dm_db_missing_index_details.  
  
Notamment, si une requête contient des prédicats d'égalité qui impliquent un sous-ensemble de colonnes clés d'index ou si elle contient des prédicats d'inégalité qui impliquent des colonnes clés d'index, l'index HASH ne peut pas être utilisé tel quel, et un autre index est requis pour exécuter la requête efficacement.  
  
**Solution de contournement :** si vous utilisez des index hach, inspectez les requêtes et les plans de requête pour déterminer si les requêtes peuvent tirer parti des opérations de recherche d'index sur un sous-ensemble de la clé d'index, ou des opérations de recherche d'index sur les prédicats d'inégalité. Si vous devez effectuer une recherche sur un sous-ensemble de la clé d'index, utilisez un index NONCLUSTERED, ou un index HASH uniquement sur les colonnes qui font l'objet de votre recherche. Si vous devez effectuer une recherche sur un prédicat d'inégalité, utilisez un index NONCLUSTERED au lieu d'un index HASH.  
  
#### <a name="325-failure-when-using-a-memory-optimized-table-and-memory-optimized-table-variable-in-the-same-query-if-the-database-option-readcommittedsnapshot-is-set-to-on"></a>3.2.5 Échec lors de l'utilisation d'une table mémoire optimisée et d'une variable de table mémoire optimisée dans la même requête, si l'option de base de données READ_COMMITTED_SNAPSHOT a la valeur ON  
**Problème :** si l'option de base de données READ_COMMITTED_SNAPSHOT a la valeur ON et que vous accédez à une table mémoire optimisée et à une variable de table mémoire optimisée dans la même instruction en dehors du contexte d'une transaction utilisateur, vous pouvez obtenir ce message d'erreur :  
  
```  
Msg 41359  
A query that accesses memory optimized tables using the READ COMMITTED  
isolation level, cannot access disk based tables when the database option  
READ_COMMITTED_SNAPSHOT is set to ON. Provide a supported isolation level  
for the memory optimized table using a table hint, such as WITH (SNAPSHOT).  
```  
  
**Solution de contournement :** utilisez l'indicateur de table WITH (SNAPSHOT) avec la variable de table ou définissez l'option de base de données MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT sur ON à l'aide de l'instruction suivante :  
  
```  
ALTER DATABASE CURRENT   
SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT=ON  
```  
  
#### <a name="326-procedure-and-query-execution-statistics-for-natively-compiled-stored-procedures-record-worker-time-in-multiples-of-1000"></a>3.2.6 Les statistiques d'exécution des procédures et des requêtes pour les procédures stockées compilées en mode natif enregistrent le temps de travail par multiples de 1000  
**Problème :** après l'activation de la collection de procédures ou de la collection de statistiques d'exécution de requête pour les procédures stockées compilées en mode natif avec sp_xtp_control_proc_exec_stats ou sp_xtp_control_query_exec_stats, vous voyez que le *_worker_time est indiqué par multiples de 1000 dans les vues de gestion dynamique sys.dm_exec_procedure_stats et sys.dm_exec_query_stats. Les exécutions de requête dont le temps de travail est inférieur à 500 microsecondes seront indiquées avec un worker_time de 0.  
  
**Solution de contournement :** aucune. Ne comptez pas sur le worker_time indiqué dans les vues de gestion dynamique des statistiques pour les requêtes à exécution courte dans les procédures stockées compilées en mode natif.  
  
#### <a name="327-error-with-showplanxml-for-natively-compiled-stored-procedures-that-contain-long-expressions"></a>3.2.7 Erreur avec SHOWPLAN_XML pour les procédures stockées compilées en mode natif contenant des expressions longues  
**Problème :** si une procédure stockée compilée en mode natif contient une expression longue, l'obtention du SHOWPLAN_XML pour la procédure à l'aide de l'option T-SQL SHOWPLAN_XML SET ON ou de l'option « Afficher le plan d'exécution estimé » dans Management Studio peut entraîner l'erreur suivante :  
  
```  
Msg 41322. MAT/PIT export/import encountered a failure for memory  
optimized table or natively compiled stored procedure with object ID  
278292051 in database ID 6. The error code was  
0xc00cee81.  
```  
  
**Solution de contournement :** il n'existe deux solutions de contournement :  
  
1.  Ajoutez des parenthèses à l'expression, comme dans l'exemple suivant :  
  
    À la place de :  
  
    ```  
    SELECT @v0 + @v1 + @v2 + ... + @v199  
    ```  
  
    Écrivez :  
  
    ```  
    SELECT((@v0 + ... + @v49) + (@v50 + ... + @v99)) + ((@v100 + ... + @v149) + (@v150 + ... + @v199))  
    ```  
  
2.  Créez une seconde procédure avec une expression légèrement simplifiée, pour le plan d'exécution de requêtes. La forme générale du plan doit être identique. Par exemple, à la place de :  
  
    ```  
    SELECT @v0 +@v1 +@v2 +...+@v199  
    ```  
  
    Écrivez :  
  
    ```  
    SELECT @v0 +@v1  
    ```  
  
#### <a name="328-using-a-string-parameter-or-variable-with-datepart-and-related-functions-in-a-natively-compiled-stored-procedure-results-in-an-error"></a>3.2.8 L'utilisation d'un paramètre ou d'une variable avec DATEPART et des fonctions liées dans une procédure stockée compilée en mode natif génère une erreur  
**Problème :** en utilisant un paramètre ou une variable qui a un type de données de chaîne tel que (var)char ou n(var)char avec les fonctions intégrées DATEPART, DAY, MONTH, et YEAR dans une procédure stockée compilée en mode natif, vous voyez un message d'erreur indiquant que le datetimeoffset du type de données n'est pas pris en charge par les procédures stockées compilées en mode natif.  
  
**Solution de contournement :** attribuez le paramètre ou la variable de chaîne à une nouvelle variable de type datetime2, puis utilisez cette variable dans la fonction DATEPART, DAY, MONTH, ou YEAR. Par exemple :  
  
```  
DECLARE @d datetime2 = @string  
DATEPART(weekday, @d)  
```  
  
#### <a name="329-native-compilation-advisor-flags-delete-from-clauses-incorrectly"></a>3.2.9 Le Conseiller de compilation native indique les clauses DELETE FROM de façon incorrecte  
**Problème :** le Conseiller de compilation native indique les clauses DELETE FROM d'une procédure stockée comme étant incompatibles, ce qui est incorrect.  
  
**Solution de contournement :** aucune.  
  
### <a name="33-register-through-ssms-adds-dac-meta-data-with-mismatched-instance-ids"></a>3.3 L'enregistrement via SSMS ajoute des métadonnées DAC avec des ID d'instance incompatibles  
**Problème :** lors de l’enregistrement ou de la suppression d’un package d’application de la couche Données (.dacpac) via SQL Server Management Studio, les tables sysdac* ne sont pas mises à jour correctement pour permettre à un utilisateur d’interroger l’historique dacpac pour la base de données.  L’instance_id pour sysdac_history_internal et pour sysdac_instances_internal ne correspondent pas pour permettre une jointure.  
  
**Solution de contournement :** ce problème est résolu avec la redistribution du [Feature Pack de Data-Tier Application Framework](https://www.microsoft.com/download/details.aspx?id=42295).  Une fois la mise à jour appliquée, toutes les nouvelles entrées d’historique utilisent la valeur répertoriée pour l’instance_id dans la table sysdac_instances_internal.  
  
Si vous avez déjà le problème avec des valeurs d’instance_id non correspondantes, la seule façon de corriger les valeurs qui ne correspondent pas est de se connecter au serveur en tant qu’utilisateur disposant de privilèges pour écrire dans la base de données MSDB et mettre à jour les valeurs d’instance_id pour les faire correspondre.  S’il y a eu plusieurs événements d’inscription et de désinscription de la même base de données, il peut être nécessaire d’examiner la date/heure pour voir quels enregistrements correspondent aux valeurs d’instance_id actuelles.  
  
1.  Connectez-vous au serveur dans SQL Server Management Studio avec une connexion qui possède des autorisations de mise à jour sur MSDB.  
  
2.  Ouvrez une nouvelle requête utilisant la base de données MSDB.  
  
3.  Exécutez cette requête pour afficher toutes vos instances DAC actives.  Recherchez l’instance que vous voulez corriger et notez l’instance_id :  
  
    `select * from` sysdac_instances_internal  
  
4.  Exécutez cette requête pour voir toutes les entrées d'historique :  
  
    `select * from` sysdac_history_internal  
  
5.  Identifiez les lignes qui doivent correspondre à l'instance que vous résolvez.  
  
6.  Mettez à jour la valeur sysdac_history_internal.instance_id avec la valeur que vous avez notée à l'étape 3 (dans la table sysdac_instances_internal) :  
  
    `update` sysdac_history_internal `set` instance_id = '\<valeur de l'étape 3>\>' `where` \<expression correspondant aux lignes que vous voulez mettre à jour\>  
  
![Icône de flèche utilisée avec le lien Retour au début](../sql-server/media/uparrow16x16.gif "Icône de flèche utilisée avec le lien Retour au début")[Début](#top)  
  
## <a name="SSRS"></a>4.0 Reporting Services  
  
### <a name="41-the-sql-server-2012-reporting-services-native-mode-report-server-cannot-run-side-by-side-with-sql-server-2014-reporting-services-sharepoint-components"></a>4.1 Le serveur de rapports SQL Server 2012 Reporting Services en mode natif ne peut pas opérer côte à côte avec les composants SQL Server 2014 Reporting Services SharePoint  
**Problème** le service Windows en mode natif [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] « SQL Server Reporting Services » (ReportingServicesService.exe) ne démarre pas s'il existe des composants [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint installés sur le même serveur.  
  
**Solution de contournement :** désinstallez les composants [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint et redémarrez le service Windows Microsoft SQL Server 2012 Reporting Services.  
  
**Informations supplémentaires :**  
  
[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Le mode natif ne peut pas fonctionner côte à côte avec l'un des éléments suivants :  
  
-   [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Complément pour les produits SharePoint  
  
-   [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Service partagé SharePoint  
  
L'installation côte à côte empêche le service Windows [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] en mode natif de démarrer. Des messages d'erreur similaires aux messages suivants s'affichent dans le journal des événements Windows :  
  
```  
Log Name:   Application  
Source:          Report Server (<SQL instance ID>)  
Event ID:        117  
Task Category:   Startup/Shutdown  
Level:           Error  
Keywords:        Classic  
Description:     The report server database is an invalid version.  
  
Log Name:      Application  
Source:        Report Server (<SQL instance ID>)  
Event ID:      107  
Task Category: Management  
Level:         Error  
Keywords:      Classic  
Description:   Report Server (DENALI) cannot connect to the report server database.  
```  
  
Pour plus d'informations, consultez [Conseils, astuces et dépannage pour SQL Server 2014 Reporting Services](http://go.microsoft.com/fwlink/?LinkID=391254).  
  
### <a name="42-required-upgrade-order-for-multi-node-sharepoint-farm-to-sql-server-2014-reporting-services"></a>4.2 Ordre de mise à niveau requis pour la batterie de serveurs à plusieurs nœuds SharePoint vers SQL Server 2014 Reporting Services  
**Problème :** la génération de rapport dans une batterie de serveurs à plusieurs nœuds échoue si les instances du service partagé SharePoint [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] sont mises à niveau avant toutes les instances du complément [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour les produits SharePoint.  
  
**Solution de contournement :** dans une batterie de serveurs SharePoint à plusieurs nœuds :  
  
1.  Mettez d'abord à niveau toutes les instances du complément [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] pour les produits SharePoint.  
  
2.  Mettez ensuite à niveau toutes les instances du service partagé [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint.  
  
Pour plus d'informations, consultez [Conseils, astuces et dépannage pour SQL Server 2014 Reporting Services](http://go.microsoft.com/fwlink/?LinkID=391254).  
  
![Icône de flèche utilisée avec le lien Retour au début](../sql-server/media/uparrow16x16.gif "Icône de flèche utilisée avec le lien Retour au début")[Début](#top)  
  
## <a name="AzureVM"></a>5.0 SQL Server 2014 RTM sur des machines virtuelles Microsoft Azure  
  
### <a name="51-the-add-azure-replica-wizard-returns-an-error-when-configuring-an-availability-group-listener-in-windows-azure"></a>5.1 L'Assistant Ajouter un réplica Windows Azure retourne une erreur lors de la configuration d'un écouteur de groupe de disponibilité dans Windows Azure  
**Problème :** si un groupe de disponibilité a un écouteur, l'Assistant Ajouter un réplica Windows Azure renvoie une erreur lorsque vous tentez de configurer l'écouteur dans Windows Azure.  
  
Cela est dû au fait que les écouteurs du groupe de disponibilité ont besoin d'une adresse IP dans chaque sous-réseau qui héberge des réplicas de groupe de disponibilité, y compris le sous-réseau Azure.  
  
**Solution de contournement :**  
  
1.  Dans la page de l'écouteur, attribuez une adresse IP statique libre dans le sous-réseau Azure qui hébergera le réplica de groupe de disponibilité à l'écouteur du groupe de disponibilité.  
  
    Cela permet à l'Assistant d'ajouter le réplica dans Windows Azure.  
  
2.  Une fois l'Assistant terminé, vous devez achever la configuration de l'écouteur dans Windows Azure comme expliqué dans la rubrique [Configuration de l'écouteur pour les groupes de disponibilité AlwaysOn dans Windows Azure](http://msdn.microsoft.com/library/dn376546.aspx)  
  
![Icône de flèche utilisée avec le lien Retour au début](../sql-server/media/uparrow16x16.gif "Icône de flèche utilisée avec le lien Retour au début")[Début](#top)  
  
## <a name="SSAS"></a>6.0 Analysis Services  
  
### <a name="61-msolap5-must-be-downloaded-installed-and-registered-for-a-sharepoint-2010-new-farm-configured-with-sql-server-2014"></a>6.1 MSOLAP.5 doit être téléchargé, installé et inscrit pour une nouvelle batterie de serveurs SharePoint 2010 configurée avec SQL Server 2014  
**Problème :**  
  
-   Pour une batterie de serveurs SharePoint 2010 configurée avec un déploiement SQL Server 2014 RTM, les classeurs PowerPivot ne peuvent pas se connecter aux modèles de données, car le fournisseur référencé dans la chaîne de connexion n'est pas installé.  
  
**Solution de contournement :**  
  
1.  Téléchargez le fournisseur MSOLAP.5 à partir du Feature Pack [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] . Installez le fournisseur sur les serveurs d'applications exécutant Excel Services. Pour plus d'informations, consultez la section « Fournisseur Microsoft Analysis Services OLE DB pour Microsoft SQL Server 2012 SP1 » [Feature Pack de Microsoft SQL Server 2012 SP1](http://www.microsoft.com/download/details.aspx?id=35580).  
  
2.  Inscrivez MSOLAP.5 en tant que fournisseur approuvé dans SharePoint Excel Services. Pour plus d'informations, consultez [Ajouter MSOLAP.5 en tant que fournisseur de données approuvé dans Excel Services](http://technet.microsoft.com/library/hh758436.aspx).  
  
**Informations supplémentaires :**  
  
-   [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] contient MSOLAP.6. [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] et [!INCLUDE[ssSQL14](../includes/sssql14-md.md)][!INCLUDE[ssGemini](../includes/ssgemini-md.md)] utilisent MSOLAP.5. Si MSOLAP.5 n'est pas installé sur l'ordinateur exécutant Excel Services, Excel Services ne peut pas charger les modèles de données.  
  
### <a name="62-msolap5-must-be-downloaded-installed-and-registered-for-a-sharepoint-2013-new-farm-configured-with-sql-server-2014"></a>6.2 MSOLAP.5 doit être téléchargé, installé et enregistré pour une nouvelle batterie de serveurs SharePoint 2013 configurée avec SQL Server 2014  
**Problème :**  
  
-   Pour une batterie de serveurs SharePoint 2013 configurée avec un déploiement [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] , les classeurs Excel référençant le fournisseur MSOLAP.5 ne peuvent pas se connecter aux modèles de données tabulaires, car le fournisseur référencé dans la chaîne de connexion n'est pas installé.  
  
**Solution de contournement :**  
  
1.  Téléchargez le fournisseur MSOLAP.5 à partir du Feature Pack [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] . Installez le fournisseur sur les serveurs d'applications exécutant Excel Services. Pour plus d'informations, consultez la section « Fournisseur Microsoft Analysis Services OLE DB pour Microsoft SQL Server 2012 SP1 » [Feature Pack de Microsoft SQL Server 2012 SP1](http://www.microsoft.com/download/details.aspx?id=35580).  
  
2.  Inscrivez MSOLAP.5 en tant que fournisseur approuvé dans SharePoint Excel Services. Pour plus d'informations, consultez [Ajouter MSOLAP.5 en tant que fournisseur de données approuvé dans Excel Services](http://technet.microsoft.com/library/hh758436.aspx).  
  
**Informations supplémentaires :**  
  
-   [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] contient MSOLAP.6. mais les classeurs PowerPivot SQL Server 2014 utilisent MSOLAP.5. Si MSOLAP.5 n'est pas installé sur l'ordinateur exécutant Excel Services, Excel Services ne peut pas charger les modèles de données.  
  
### <a name="63-corrupt-data-refresh-schedules"></a>6.3 La planification de l'actualisation des données est corrompue  
**Problème :**  
  
-   Vous mettez jour une planification de l'actualisation et la planification est endommagée et inutilisable.  
  
**Solution de contournement :**  
  
1.  Dans Microsoft Excel, supprimez les propriétés avancées personnalisées. Consultez la section « Solution de contournement » de l'article suivant de la Base de connaissances [2927748 Ko](http://support.microsoft.com/kb/2927748).  
  
**Informations supplémentaires :**  
  
-   Lorsque vous mettez à jour une planification de l'actualisation des données d'un classeur, si la longueur sérialisée de la planification d'actualisation est inférieure à la planification d'origine, la taille du tampon n'est pas correctement mise à jour et les nouvelles informations de planification sont fusionnées avec les anciennes informations de planification, ce qui endommage la planification.  
  
![Icône de flèche utilisée avec le lien Retour au début](../sql-server/media/uparrow16x16.gif "Icône de flèche utilisée avec le lien Retour au début")[Début](#top)  
  
## <a name="DQS"></a>7.0 Data Quality Services  
  
### <a name="71-no-cross-version-support-for-data-quality-services-in-master-data-services"></a>7.1 Pas de prise en charge des inter-versions pour Data Quality Services dans Master Data Services  
**Problème :** les scénarios suivants ne sont pas pris en charge :  
  
-   Master Data Services 2014 hébergé dans une base de données du moteur de base de données SQL Server dans SQL Server 2012 avec Data Quality Services 2012.  
  
-   Master Data Services 2012 hébergé dans une base de données du moteur de base de données SQL Server dans SQL Server 2014 avec Data Quality Services 2014 installé.  
  
**Solution de contournement :** utilisez la même version de Master Data Services que la base de données du moteur de base de données et Data Quality Services.  
  
![Icône de flèche utilisée avec le lien Retour au début](../sql-server/media/uparrow16x16.gif "Icône de flèche utilisée avec le lien Retour au début")[Début](#top)  
  
## <a name="UA"></a>8.0 Problèmes relatifs au Conseiller de mise à niveau  
  
### <a name="81--sql-server-2014-upgrade-advisor-reports-irrelevant-upgrade-issues-for-sql-server-reporting-services"></a>8.1 Le Conseiller de mise à niveau de SQL Server 2014 signale des problèmes de mise à niveau non pertinents pour SQL Server Reporting Services  
**Problème :** le Conseiller de mise à niveau SQL Server (SSUA) fourni avec le support de SQL Server 2014 signale incorrectement plusieurs erreurs lors de l'analyse du serveur SQL Server Reporting Services.  
  
**Solution de contournement :** ce problème est résolu dans le Conseiller de mise à niveau fourni dans le [Feature Pack de SQL Server 2014 pour SSUA](http://go.microsoft.com/fwlink/?LinkID=306709).  
  
### <a name="82--sql-server-2014-upgrade-advisor-reports-an-error-when-analyzing-sql-server-integration-services-server"></a>8.2 Le Conseiller de mise à niveau de SQL Server 2014 signale une erreur lors de l'analyse du serveur SQL Server Integration Services  
**Problème :** le Conseiller de mise à niveau SQL Server (SSUA) fourni avec le média de SQL Server 2014 signale une erreur lors de l’analyse du serveur SQL Server Integration Services.  L’erreur affichée à l’utilisateur est la suivante :  
  
```  
The installed version of Integration Services does not support Upgrade Advisor.   
The assembly information is "Microsoft.SqlServer.ManagedDTS, Version=11.0.0.0,   
Culture=neutral, PublicKeyToken=89845dcd8080cc91  
```  
  
**Solution de contournement :** ce problème est résolu dans le Conseiller de mise à niveau fourni dans le [Feature Pack de SQL Server 2014 pour SSUA](http://go.microsoft.com/fwlink/?LinkID=306709).  
  
![Icône de flèche utilisée avec le lien Retour au début](../sql-server/media/uparrow16x16.gif "Icône de flèche utilisée avec le lien Retour au début")[Début](#top)  
  
[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
