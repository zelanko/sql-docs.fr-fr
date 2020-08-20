---
description: Utilisation de IMultipleResults pour traiter plusieurs jeux de résultats dans SQL Server Native Client
title: IMultipleResults, jeux de résultats multiples
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- IMultipleResults interface
- multiple-rowset results
ms.assetid: 754d3f30-7d94-4b67-8dac-baf2699ce9c6
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 885ec9a1130c7e1f3db6bbbbebbe9a0190bd2ec4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88455781"
---
# <a name="using-imultipleresults-to-process-multiple-result-sets-in-sql-server-native-client"></a>Utilisation de IMultipleResults pour traiter plusieurs jeux de résultats dans SQL Server Native Client
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Les consommateurs utilisent l’interface **IMultipleResults** pour traiter les résultats retournés par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB exécution de la commande du fournisseur. Lorsque le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client soumet une commande pour l’exécution, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] exécute les instructions et retourne les résultats.  
  
 Un client doit traiter tous les résultats d'exécution de commande. Étant donné que l’exécution de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] commande du fournisseur OLE DB Native Client peut générer des objets à plusieurs ensembles de lignes en tant que résultats, utilisez l’interface **IMultipleResults** pour vous assurer que la récupération des données d’application termine l’aller-retour initié par le client.  
  
 L’instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante génère plusieurs ensembles de lignes, certains contenant les données de ligne de la table **OrderDetails** et d’autres les résultats de la clause COMPUTE BY :  
  
```sql
SELECT OrderID, FullPrice = (UnitPrice * Quantity), Discount,  
    Discounted = UnitPrice * (1 - Discount) * Quantity  
FROM OrderDetails  
ORDER BY OrderID  
COMPUTE  
    SUM(UnitPrice * Quantity), SUM(UnitPrice * (1 - Discount) * Quantity)  
    BY OrderID  
```  
  
 Si un consommateur exécute une commande contenant ce texte et demande un ensemble de lignes comme interface de résultats retournée, seul le premier jeu de lignes est retourné. Le consommateur peut traiter toutes les lignes dans l'ensemble de lignes retourné. Toutefois, si la propriété de la source de données DBPROP_MULTIPLECONNECTIONS est définie sur VARIANT_FALSE et que MARS n’est pas activé sur la connexion, aucune autre commande ne peut être exécutée sur l’objet session (le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client ne crée pas une autre connexion) tant que la commande n’est pas annulée. Si MARS n’est pas activé sur la connexion, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client retourne une erreur de DB_E_OBJECTOPEN si DBPROP_MULTIPLECONNECTIONS est VARIANT_FALSE et retourne E_FAIL s’il existe une transaction active.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client retournera également DB_E_OBJECTOPEN lors de l’utilisation de paramètres de sortie diffusés en continu et l’application n’a pas consommé toutes les valeurs de paramètres de sortie retournées avant d’appeler **IMultipleResults :: GetResults** pour obtenir le jeu de résultats suivant. Si MARS n'est pas activé et que la connexion est occupée à exécuter une commande qui ne produit pas un ensemble de lignes ou produit un ensemble de lignes qui n'est pas un curseur côté serveur, et que la propriété de la source de données DBPROP_MULTIPLECONNECTIONS a la valeur VARIANT_TRUE, le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client crée des connexions supplémentaires pour prendre en charge les objets de commande concurrentiels à moins qu'une transaction ne soit active, auquel cas une erreur est retournée. Les transactions et le verrouillage sont gérés par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion par connexion. Si une deuxième connexion est générée, la commande sur les connexions séparées ne partage pas les verrous. Prenez soin de vérifier qu'une commande n'en bloque pas une autre en maintenant les verrous sur les lignes demandées par l'autre commande. Si MARS est activé, plusieurs commandes peuvent être actives sur les connexions et si les transactions explicites sont utilisées, les commandes partagent toutes une transaction commune.  
  
 Le consommateur peut annuler la commande en utilisant [ISSAbort::Abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md) ou en libérant toutes les références détenues sur l’objet de commande et l’ensemble de lignes dérivé.  
  
 L’utilisation de **IMultipleResults** dans toutes les instances permet au consommateur d’obtenir tous les ensembles de lignes générés par l’exécution de la commande et permet aux consommateurs de déterminer de façon appropriée à quel moment annuler l’exécution de la commande et libérer un objet session en vue d’une utilisation par d’autres commandes.  
  
> [!NOTE]  
>  Lorsque vous utilisez les curseurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'exécution de commande crée le curseur. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne une valeur indiquant si la création du curseur a réussi ou échoué ; par conséquent, l'aller-retour vers l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se termine au retour de l'exécution de commande. Chaque appel de **GetNextRows** devient alors un aller-retour. De cette façon, plusieurs objets de commande actifs peuvent exister, chacun traitant un ensemble de lignes qui est le résultat d'une extraction du curseur côté serveur. Pour plus d’informations, consultez [Ensembles de lignes et curseurs SQL Server](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes](../../relational-databases/native-client-ole-db-commands/commands.md)  
  
  
