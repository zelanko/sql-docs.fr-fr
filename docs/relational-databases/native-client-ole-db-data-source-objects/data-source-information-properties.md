---
title: Propriétés d’informations sur la Source de données | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- information properties [OLE DB]
- OLE DB data source properties [SQL Server Native Client]
ms.assetid: 7fd80e47-5bd9-41e2-a3d3-091a7c8c5f2b
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5454f7c41a55442c8b68cd57dd71c3859902be97
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52535113"
---
# <a name="data-source-information-properties"></a>Propriétés des informations de la source de données
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Dans le jeu de propriétés DBPROPSET_SQLSERVERDATASOURCEINFO spécifique au fournisseur, le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client définit les propriétés des informations de la source de données.  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|SSPROP_COLUMNLEVELCOLLATION|Type : VT_BOOL<br /><br /> R/W (Lecture/écriture) : Lire<br /><br /> Valeur par défaut : VARIANT_TRUE<br /><br /> Description : Utilisé pour déterminer si le classement de colonne est pris en charge.<br /><br /> VARIANT_TRUE : Classement au niveau des colonnes est pris en charge.<br /><br /> VARIANT_FALSE : Classement au niveau des colonnes n’est pas pris en charge.|  
|SSPROP_UNICODELCID|Type : VT_I4 R/W : Lire<br /><br /> Description : ID de paramètres régionaux Unicode.<br /><br /> Il s'agit des paramètres régionaux utilisés pour le tri des données Unicode.|  
|SSPROP_UNICODECOMPARISONSTYLE|Type : VT_I4 R/W : Lire<br /><br /> Description : Style de comparaison Unicode.<br /><br /> Options de tri utilisés pour le tri des données Unicode.|  
  
 Dans le jeu de propriétés DBPROPSET_SQLSERVERSTREAM spécifique au fournisseur, le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client définit la propriété supplémentaire suivante.  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|SSPROP_STREAM_XMLROOT|Type : VT_BSTR R/W : Lecture/Écriture<br /><br /> Description : Le résultat d’une requête FOR XML ne peut pas être un document bien formé. Lorsque cette propriété est spécifiée, le résultat d’une requête 'select … for XML' est encapsulé dans la balise racine fournie par cette propriété pour retourner un document XML bien formé. Si la requête est exécutée dans le navigateur, il se peut que le navigateur affiche les erreurs de l'analyseur lors du chargement du résultat. Pour éviter l'erreur, SQL ISAPI prend en charge le mot clé ROOT. Ce mot clé est mappé avec la propriété SSPROP_STREAM_XMLROOT.|  
  
## <a name="see-also"></a>Voir aussi  
 [Objets Source de données &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
