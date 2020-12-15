---
description: Propriétés des informations sur la source de données (fournisseur Native Client OLE DB)
title: Propriétés des informations de la source de données (fournisseur OLE DB Native Client) | Microsoft Docs
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 69943bc28ca5badecd2cb1406ddd074301fc828c
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97469420"
---
#  <a name="sql-server-native-client-data-source-information-properties"></a>SQL Server Native Client les propriétés des informations de source de données
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Dans le jeu de propriétés DBPROPSET_SQLSERVERDATASOURCEINFO spécifique au fournisseur, le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client définit les propriétés des informations de la source de données.  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|SSPROP_COLUMNLEVELCOLLATION|Type : VT_BOOL<br /><br /> R/W : Read (Lecture)<br /><br /> Valeur par défaut : VARIANT_TRUE<br /><br /> Description : utilisé pour déterminer si le classement des colonnes est pris en charge.<br /><br /> VARIANT_TRUE : le classement au niveau des colonnes est pris en charge.<br /><br /> VARIANT_FALSE : le classement au niveau des colonnes n'est pas pris en charge.|  
|SSPROP_UNICODELCID|Type : VT_I4 R/W: Read (Lecture)<br /><br /> Description : ID des paramètres régionaux Unicode.<br /><br /> Il s'agit des paramètres régionaux utilisés pour le tri des données Unicode.|  
|SSPROP_UNICODECOMPARISONSTYLE|Type : VT_I4 R/W: Read (Lecture)<br /><br /> Description : style de comparaison Unicode.<br /><br /> Options de tri utilisés pour le tri des données Unicode.|  
  
 Dans le jeu de propriétés DBPROPSET_SQLSERVERSTREAM spécifique au fournisseur, le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client définit la propriété supplémentaire suivante.  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|SSPROP_STREAM_XMLROOT|Type : VT_BSTR R/W: Read/Write (Lecture/écriture)<br /><br /> Description : le résultat d'une requête FOR XML ne peut pas être un document bien formé. Lorsque cette propriété est spécifiée, le résultat d'une requête 'select... for XML' est encapsulée dans la balise racine fournie par la propriété pour retourner un document XML bien formé. Si la requête est exécutée dans le navigateur, il se peut que le navigateur affiche les erreurs de l'analyseur lors du chargement du résultat. Pour éviter l'erreur, SQL ISAPI prend en charge le mot clé ROOT. Ce mot clé est mappé avec la propriété SSPROP_STREAM_XMLROOT.|  
  
## <a name="see-also"></a>Voir aussi  
 [Objets source de données &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
