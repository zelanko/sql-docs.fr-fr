---
title: Propriétés de session, SQL Native Client OLE DB
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4d4b2bef0bf37b4400ac2cfcb672e43ba4f5abcb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297130"
---
# <a name="session-properties---sql-server-native-client-ole-db-provider"></a>Propriétés de la session - Fournisseur OLE DB de SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur native De DB OLE de client interprète les propriétés de session OLE DB comme suit.  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|DBPROP_SESS_AUTOCOMMITISOLEVELS|Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur native Client OLE DB prend en charge tous les niveaux d’isolement des transactions automatiques, à l’exception du niveau de chaos DBPROPVAL_TI_CHAOS.|  
|||

 Dans l’ensemble de propriétés spécifique [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au fournisseur DBPROPSET_SQLSERVERSESSION, le fournisseur de DB OLE de client autochtone définit la propriété de session supplémentaire suivante.  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|SSPROP_QUOTEDCATALOGNAMES|Type : VT_BOOL<br /><br /> R/W : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : identificateurs entre guillemets autorisés dans la restriction CATALOG.<br /><br /> VARIANT_TRUE : les identificateurs entre guillemets sont reconnus pour une restriction de catalogue pour les ensembles de lignes de schéma qui fournissent la prise en charge des requêtes distribuées.<br /><br /> VARIANT_FALSE : les identificateurs entre guillemets ne sont pas reconnus pour une restriction de catalogue pour les ensembles de lignes de schéma qui fournissent la prise en charge des requêtes distribuées.<br /><br /> Pour plus d’informations sur les ensembles de lignes de schéma qui fournissent la prise en charge des requêtes distribuées, consultez [Prise en charge des requêtes distribuées dans les ensembles de lignes de schéma](../../relational-databases/native-client/ole-db/schema-rowsets-distributed-query-support.md).|  
|SSPROP_ALLOWNATIVEVARIANT|Type : VT_BOOL<br /><br /> Lecture/écriture : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : détermine si les données sont extraites en tant que DBTYPE_VARIANT ou DBTYPE_SQLVARIANT.<br /><br /> VARIANT_TRUE : le type de colonne est retourné en tant que DBTYPE_SQLVARIANT, auquel cas la mémoire tampon contient la structure SSVARIANT.<br /><br /> VARIANT_FALSE : le type de colonne est retourné en tant que DBTYPE_VARIANT et la mémoire tampon a la structure VARIANT.|  
|SSPROP_ASYNCH_BULKCOPY|Pour utiliser le mode asynchrone, affectez la valeur VARIANT_TRUE à la propriété de session spécifique au fournisseur SSPROP_ASYNCH_BULKCOPY avant d'appeler la méthode BCPExec. Cette propriété est disponible dans le jeu de propriétés DBPROPSET_SQLSERVERSESSION.|  
|||

## <a name="see-also"></a>Voir aussi  
 [Objets source de données &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
