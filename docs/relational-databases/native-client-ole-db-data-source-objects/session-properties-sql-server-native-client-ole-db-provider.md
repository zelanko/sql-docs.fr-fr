---
title: Propriétés de la session - fournisseur de SQL Server Native Client OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- sessions [OLE DB]
- SQL Server Native Client OLE DB provider, sessions
ms.assetid: 2498fbad-b3db-4bea-8fc6-fef5317d3eba
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d17b673a12a915318e523000081fcd6114e8185c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68128553"
---
# <a name="session-properties---sql-server-native-client-ole-db-provider"></a>Propriétés de la session - Fournisseur OLE DB de SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les fournisseur OLE DB Native Client interprète les propriétés de session OLE DB comme suit.  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|DBPROP_SESS_AUTOCOMMITISOLEVELS|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif prend en charge tous les niveaux d’isolation de transaction autocommit à l’exception du niveau de chaos DBPROPVAL_TI_CHAOS.|  
  
 Dans la propriété spécifique au fournisseur de jeu de propriétés DBPROPSET_SQLSERVERSESSION, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif définit la propriété de session supplémentaire suivante.  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|SSPROP_QUOTEDCATALOGNAMES|Tapez : VT_BOOL<br /><br /> R/W : en lecture/écriture<br /><br /> Par défaut : VARIANT_FALSE<br /><br /> Description : Identificateurs entre guillemets autorisés dans la restriction de catalogue.<br /><br /> VARIANT_TRUE : Identificateurs entre guillemets sont reconnus pour une restriction de catalogue pour les ensembles de lignes de schéma qui fournissent la prise en charge des requêtes distribuées.<br /><br /> VARIANT_FALSE : Identificateurs entre guillemets ne sont pas reconnus pour une restriction de catalogue pour les ensembles de lignes de schéma qui fournissent la prise en charge des requêtes distribuées.<br /><br /> Pour plus d’informations sur les ensembles de lignes de schéma qui fournissent la prise en charge des requêtes distribuées, consultez [Prise en charge des requêtes distribuées dans les ensembles de lignes de schéma](../../relational-databases/native-client/ole-db/schema-rowsets-distributed-query-support.md).|  
|SSPROP_ALLOWNATIVEVARIANT|Tapez : VT_BOOL<br /><br /> R/W : En lecture/écriture<br /><br /> Par défaut : VARIANT_FALSE<br /><br /> Description : Détermine si les données sont extraites en tant que DBTYPE_VARIANT ou DBTYPE_SQLVARIANT.<br /><br /> VARIANT_TRUE : Type de colonne est retourné en tant que DBTYPE_SQLVARIANT dans lequel cas la mémoire tampon contiendra une structure SSVARIANT.<br /><br /> VARIANT_FALSE : Type de colonne est retourné en tant que DBTYPE_VARIANT et la mémoire tampon a la structure VARIANT.|  
|SSPROP_ASYNCH_BULKCOPY|Pour utiliser le mode asynchrone, affectez la valeur VARIANT_TRUE à la propriété de session spécifique au fournisseur SSPROP_ASYNCH_BULKCOPY avant d'appeler la méthode BCPExec. Cette propriété est disponible dans le jeu de propriétés DBPROPSET_SQLSERVERSESSION.|  
  
## <a name="see-also"></a>Voir aussi  
 [Objets Source de données &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
