---
title: Création d’ensembles de lignes avec ICommand::Execute | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
- Execute method
ms.assetid: 9b530b7d-8165-49d4-a978-5ced17c6705e
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b2be5161bd84a6bd2fe2bcc87c494ddebe9e7787
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47674217"
---
# <a name="creating-rowsets-with-icommandexecute"></a>Création d'ensembles de lignes avec ICommand::Execute
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Pour les ensembles de lignes créés avec la méthode **ICommand::Execute**, les propriétés souhaitées dans l’ensemble de lignes résultant peuvent limiter le texte de la commande. Cela est particulièrement important pour les consommateurs qui prennent en charge un texte de commande dynamique.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif ne peut pas utiliser [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] curseurs pour prendre en charge les résultats de plusieurs ensembles de lignes générés par de nombreuses commandes. Lorsqu'un consommateur demande un ensemble de lignes qui requiert la prise en charge de curseurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], une erreur se produit si le texte de commande génère plusieurs ensembles de lignes comme résultat. Pour plus d’informations, consultez [commandes générant plusieurs ensembles de lignes résultats](../../relational-databases/native-client-ole-db-commands/commands-generating-multiple-rowset-results.md).  
  
 Défilement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ensembles de lignes de fournisseur OLE DB Native Client sont prises en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les curseurs. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] impose des limitations aux curseurs qui sont sensibles aux modifications effectuées par d'autres utilisateurs de la base de données. En particulier, dans certains curseurs, les lignes ne peuvent pas être triées ; en outre, toute tentative de création d'un ensemble de lignes à l'aide d'une commande qui contient une clause SQL ORDER BY peut échouer. Pour plus d’informations, consultez [Ensembles de lignes et curseurs SQL Server](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Ensembles de lignes](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
