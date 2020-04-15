---
title: IMultipleResults, ensembles de résultats multiples
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
ms.openlocfilehash: c5e19cef4e00fc1c55e29e51ccea13c2fdb7a0e2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304443"
---
# <a name="using-imultipleresults-to-process-multiple-result-sets"></a>Utilisation d'IMultipleResults pour traiter plusieurs jeux de résultats
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Les consommateurs utilisent l’interface **IMultipleResults** pour traiter les résultats retournés par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’exécution de commande du fournisseur native Client OLE DB. Lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le fournisseur de DB OLE du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client autochtone soumet une commande pour exécution, exécute les relevés et renvoie tous les résultats.  
  
 Un client doit traiter tous les résultats d'exécution de commande. Étant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] donné que l’exécution de commande du fournisseur de fournisseurs OLE DB du client autochtone peut générer des objets à plusieurs rangées comme résultats, utilisez l’interface **IMultipleResults** pour vous assurer que la récupération des données d’application complète l’aller-retour initié par le client.  
  
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
  
 Si un consommateur exécute une commande contenant ce texte et demande un ensemble de lignes comme interface de résultats retournée, seul le premier jeu de lignes est retourné. Le consommateur peut traiter toutes les lignes dans l'ensemble de lignes retourné. Mais, si la propriété DBPROP_MULTIPLECONNECTIONS source de données est réglée pour VARIANT_FALSE, et MARS n’est pas activé sur la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion, aucune autre commande ne peut être exécutée sur l’objet de session (le fournisseur de DB OLE du client autochtone ne créera pas une autre connexion) jusqu’à ce que la commande soit annulée. Si MARS n’est pas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] activé sur la connexion, le fournisseur de DB OLE de client autochtone renvoie une erreur de DB_E_OBJECTOPEN si DBPROP_MULTIPLECONNECTIONS est VARIANT_FALSE et retourne E_FAIL s’il y a une transaction active.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur native Client OLE DB retournera également DB_E_OBJECTOPEN lors de l’utilisation des paramètres de sortie en streaming et l’application n’a pas consommé toutes les valeurs de paramètres de sortie retournées avant d’appeler **IMultipleResults::GetResults** pour obtenir le prochain ensemble de résultats. Si MARS n'est pas activé et que la connexion est occupée à exécuter une commande qui ne produit pas un ensemble de lignes ou produit un ensemble de lignes qui n'est pas un curseur côté serveur, et que la propriété de la source de données DBPROP_MULTIPLECONNECTIONS a la valeur VARIANT_TRUE, le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client crée des connexions supplémentaires pour prendre en charge les objets de commande concurrentiels à moins qu'une transaction ne soit active, auquel cas une erreur est retournée. Les transactions et le verrouillage sont gérés par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion par connexion. Si une deuxième connexion est générée, la commande sur les connexions séparées ne partage pas les verrous. Prenez soin de vérifier qu'une commande n'en bloque pas une autre en maintenant les verrous sur les lignes demandées par l'autre commande. Si MARS est activé, plusieurs commandes peuvent être actives sur les connexions et si les transactions explicites sont utilisées, les commandes partagent toutes une transaction commune.  
  
 Le consommateur peut annuler la commande en utilisant [ISSAbort::Abort](../../relational-databases/native-client-ole-db-interfaces/issabort-abort-ole-db.md) ou en libérant toutes les références détenues sur l’objet de commande et l’ensemble de lignes dérivé.  
  
 L’utilisation de **IMultipleResults** dans toutes les instances permet au consommateur d’obtenir tous les ensembles de lignes générés par l’exécution de la commande et permet aux consommateurs de déterminer de façon appropriée à quel moment annuler l’exécution de la commande et libérer un objet session en vue d’une utilisation par d’autres commandes.  
  
> [!NOTE]  
>  Lorsque vous utilisez les curseurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'exécution de commande crée le curseur. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne une valeur indiquant si la création du curseur a réussi ou échoué ; par conséquent, l'aller-retour vers l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se termine au retour de l'exécution de commande. Chaque appel de **GetNextRows** devient alors un aller-retour. De cette façon, plusieurs objets de commande actifs peuvent exister, chacun traitant un ensemble de lignes qui est le résultat d'une extraction du curseur côté serveur. Pour plus d’informations, consultez [Ensembles de lignes et curseurs SQL Server](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes](../../relational-databases/native-client-ole-db-commands/commands.md)  
  
  
