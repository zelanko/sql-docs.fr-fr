---
title: Catalog.cleanup_server_log | Documents Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0dedb685-d3a6-4bd6-8afd-58d98853deee
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 1195bbfcc77cb6b96ea5a68cd1a95c2b2126a81e
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogcleanupserverlog"></a>Catalog.cleanup_server_log
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Nettoie les journaux des opérations pour que la base de données SSISDB soit dans un état qui autorise la modification de la valeur de la propriété SERVER_OPERATION_ENCRYPTION_LEVEL.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql
catalog.cleanup_server_log  
```  
  
## <a name="arguments"></a>Arguments  
 Aucun.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 pour réussite et 1 pour échec.  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucun.  
  
## <a name="permissions"></a>Permissions  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations READ et EXECUTE sur le projet et, le cas échéant, les autorisations de lecture sur l’environnement référencé.  
  
-   L’appartenance à la **ssis_admin** rôle de base de données.  
  
-   L’appartenance à la **sysadmin** rôle de serveur.  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 Cette procédure stockée génère des erreurs dans les scénarios suivants :  
  
-   Il existe une ou plusieurs opérations actives dans la base de données SSISDB.  
  
-   La base de données SSISDB n’est pas en mode mono-utilisateur.  
  
## <a name="remarks"></a>Notes  
 SQL Server 2012 Service Pack 2 ajouté à la propriété SERVER_OPERATION_ENCRYPTION_LEVEL la **internal.catalog_properties** table. Cette propriété a deux valeurs possibles :  
  
-   **PER_EXECUTION (1)** : le certificat et la clé symétrique utilisée pour la protection des paramètres sensibles de l’exécution et les journaux d’exécution sont créés pour chaque exécution. Ceci est la valeur par défaut. Vous risquez de rencontrer des problèmes de performances (blocages, etc. de travaux de maintenance ayant échoué...) dans un environnement de production, car les certificats/clés sont générées pour chaque exécution. Toutefois, ce paramètre offre un niveau de sécurité supérieur à l’autre valeur (2).  
  
-   **PER_PROJECT (2)** – le certificat et la clé symétrique utilisée pour protéger les paramètres sensibles sont créés pour chaque projet. Cela vous permet de meilleures performances que le niveau PER_EXECUTION, car la clé et le certificat sont générés une fois pour un projet et non à chaque exécution.  
  
 Vous devez exécuter le [catalog.cleanup_server_log](../../integration-services/system-stored-procedures/catalog-cleanup-server-log.md) procédure stockée avant de pouvoir modifier le SERVER_OPERATION_ENCRYPTION_LEVEL comprise entre 1 et 2 (ou) à partir de 2 à 1. Avant d’exécuter cette procédure, procédez comme suit :  
  
1.  Assurez-vous que la valeur de la propriété OPERATION_CLEANUP_ENABLED est définie à TRUE dans le [catalog.catalog_properties &#40; Base de données SSISDB &#41; ](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md) table.  
  
2.  Définir la base de données Integration Services (SSISDB) pour passer en mode mono-utilisateur. Dans SQL Server Management Studio, lancer la boîte de dialogue Propriétés de la base de données pour SSISDB, basculez vers l’onglet Options et définir la propriété restreindre l’accès en mode mono-utilisateur (SINGLE_USER). Après avoir exécuté le cleanup_server_log une procédure stockée, définissez la valeur de propriété à la valeur d’origine.  
  
3.  Exécutez la procédure stockée [catalog.cleanup_server_log](../../integration-services/system-stored-procedures/catalog-cleanup-server-log.md).  
  
4.  À présent, continuez et modifier la valeur de la propriété SERVER_OPERATION_ENCRYPTION_LEVEL dans le [catalog.catalog_properties &#40; Base de données SSISDB &#41; ](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md) table.  
  
5.  Exécutez la procédure stockée [catalog.cleanup_server_execution_keys](../../integration-services/system-stored-procedures/catalog-cleanup-server-execution-keys.md) pour nettoyer les clés de certificats à partir de la base de données SSISDB. Suppression des certificats et les clés à partir de la base de données SSISDB peut prendre beaucoup de temps, donc il doit être exécuté régulièrement pendant les heures creuses.  
  
     Vous pouvez spécifier l’étendue ou le niveau (l’exécution et de projet) et le nombre de clés doit être supprimé. La taille de lot pour la suppression par défaut est 1000. Lorsque vous définissez le niveau 2, les clés et les certificats sont supprimées uniquement si les projets associés ont été supprimés.  
  
 Pour plus d’informations, consultez l’article suivant de la Base de connaissances. [CORRECTIF : Les problèmes de performances lorsque vous utilisez SSISDB comme votre déploiement stockent dans SQL Server 2012](http://support.microsoft.com/kb/2972285)  
  
## <a name="example"></a>Exemple  
 L’exemple suivant appelle la procédure stockée de cleanup_server_log.  
  
```sql  
USE [SSISDB]  
GO  
  
DECLARE@return_value int  
EXEC@return_value = [internal].[cleanup_server_log]  
SELECT'Return Value' = @return_value  
GO   
```  
  
  

