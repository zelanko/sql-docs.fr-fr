---
title: Utilisation d’IMultipleResults pour traiter plusieurs jeux de résultats | Microsoft Docs
description: Utilisation d’IMultipleResults pour traiter plusieurs jeux de résultats
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-commands
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- IMultipleResults interface
- multiple-rowset results
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 2b622e56691a54ad6db4859b8099c29645357b87
ms.sourcegitcommit: 50838d7e767c61dd0b5e677b6833dd5c139552f2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/18/2018
ms.locfileid: "39105919"
---
# <a name="using-imultipleresults-to-process-multiple-result-sets"></a>Utilisation d'IMultipleResults pour traiter plusieurs jeux de résultats
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Les consommateurs utilisent l’interface **IMultipleResults** pour traiter les résultats retournés par l’exécution de commande du pilote OLE DB pour SQL Server. Quand le pilote OLE DB pour SQL Server soumet une commande en vue de son exécution, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] exécute les instructions et retourne les résultats.  
  
 Un client doit traiter tous les résultats d'exécution de commande. Comme l’exécution d’une commande du pilote OLE DB pour SQL Server peut générer plusieurs objets d’ensembles de lignes comme résultats, utilisez l’interface **IMultipleResults** pour garantir que l’extraction de données de l’application termine la boucle initialisée par le client.  
  
 L’instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] suivante génère plusieurs ensembles de lignes, certains contenant les données de ligne de la table **OrderDetails** et d’autres les résultats de la clause COMPUTE BY :  
  
```  
SELECT OrderID, FullPrice = (UnitPrice * Quantity), Discount,  
    Discounted = UnitPrice * (1 - Discount) * Quantity  
FROM OrderDetails  
ORDER BY OrderID  
COMPUTE  
    SUM(UnitPrice * Quantity), SUM(UnitPrice * (1 - Discount) * Quantity)  
    BY OrderID  
```  
  
 Si un consommateur exécute une commande contenant ce texte et demande un ensemble de lignes comme interface de résultats retournée, seul le premier jeu de lignes est retourné. Le consommateur peut traiter toutes les lignes dans l'ensemble de lignes retourné. Cependant, si la propriété de la source de données DBPROP_MULTIPLECONNECTIONS est définie avec la valeur VARIANT_FALSE et que MARS n’est pas activé sur la connexion, aucune autre commande ne peut être exécutée sur l’objet session (le pilote OLE DB pour SQL Server ne crée pas une autre connexion) jusqu’à ce que la commande soit annulée. Si MARS n’est pas activé sur la connexion, le pilote OLE DB pour SQL Server retourne une erreur DB_E_OBJECTOPEN si DBPROP_MULTIPLECONNECTIONS a la valeur VARIANT_FALSE et retourne E_FAIL s’il existe une transaction active.  
  
 Le pilote OLE DB pour SQL Server retourne également DB_E_OBJECTOPEN lors de l’utilisation de paramètres de sortie diffusée en continu et si l’application n’a pas utilisé toutes les valeurs des paramètres de sortie retournées avant d’appeler **IMultipleResults::GetResults** pour obtenir le jeu de résultats suivant. Si MARS n’est pas activé et que la connexion est occupée à exécuter une commande qui ne produit pas un ensemble de lignes ou produit un ensemble de lignes qui n’est pas un curseur côté serveur, et que la propriété de la source de données DBPROP_MULTIPLECONNECTIONS a la valeur VARIANT_TRUE, le pilote OLE DB pour SQL Server crée des connexions supplémentaires pour prendre en charge les objets de commande concurrentiels à moins qu’une transaction ne soit active, auquel cas une erreur est retournée. Les transactions et le verrouillage sont gérés par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] connexion par connexion. Si une deuxième connexion est générée, la commande sur les connexions séparées ne partage pas les verrous. Prenez soin de vérifier qu'une commande n'en bloque pas une autre en maintenant les verrous sur les lignes demandées par l'autre commande. Si MARS est activé, plusieurs commandes peuvent être actives sur les connexions et si les transactions explicites sont utilisées, les commandes partagent toutes une transaction commune.  
  
 Le consommateur peut annuler la commande en utilisant [ISSAbort::Abort](../../oledb/ole-db-interfaces/issabort-abort-ole-db.md) ou en libérant toutes les références détenues sur l’objet de commande et l’ensemble de lignes dérivé.  
  
 L’utilisation de **IMultipleResults** dans toutes les instances permet au consommateur d’obtenir tous les ensembles de lignes générés par l’exécution de la commande et permet aux consommateurs de déterminer de façon appropriée à quel moment annuler l’exécution de la commande et libérer un objet session en vue d’une utilisation par d’autres commandes.  
  
> [!NOTE]  
>  Lorsque vous utilisez les curseurs [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], l'exécution de commande crée le curseur. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] retourne une valeur indiquant si la création du curseur a réussi ou échoué ; par conséquent, l'aller-retour vers l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] se termine au retour de l'exécution de commande. Chaque appel de **GetNextRows** devient alors un aller-retour. De cette façon, plusieurs objets de commande actifs peuvent exister, chacun traitant un ensemble de lignes qui est le résultat d'une extraction du curseur côté serveur. Pour plus d’informations, consultez [Ensembles de lignes et curseurs SQL Server](../../oledb/ole-db-rowsets/rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a> Voir aussi  
 [Commandes](../../oledb/ole-db-commands/commands.md)  
  
  
