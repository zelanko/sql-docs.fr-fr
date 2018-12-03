---
title: Propriétés d’informations sur la Source de données | Microsoft Docs
description: Propriétés des informations de la source de données
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- information properties [OLE DB]
- OLE DB data source properties [OLE DB Driver for SQL Server]
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 328a8c247fda6d67d40426cfa0f36ac47f686f11
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52516681"
---
# <a name="data-source-information-properties"></a>Propriétés des informations de la source de données
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Dans le jeu de propriétés DBPROPSET_SQLSERVERDATASOURCEINFO spécifique au fournisseur, le pilote OLE DB pour SQL Server définit les propriétés des informations de la source de données suivantes.  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|SSPROP_COLUMNLEVELCOLLATION|Type : VT_BOOL<br /><br /> R/W : Read (Lecture)<br /><br /> Valeur par défaut : VARIANT_TRUE<br /><br /> Description : utilisé pour déterminer si le classement des colonnes est pris en charge.<br /><br /> VARIANT_TRUE : le classement au niveau des colonnes est pris en charge.<br /><br /> VARIANT_FALSE : le classement au niveau des colonnes n'est pas pris en charge.|  
|SSPROP_UNICODELCID|Type : VT_I4 R/W: Read (Lecture)<br /><br /> Description : ID des paramètres régionaux Unicode.<br /><br /> Il s'agit des paramètres régionaux utilisés pour le tri des données Unicode.|  
|SSPROP_UNICODECOMPARISONSTYLE|Type : VT_I4 R/W: Read (Lecture)<br /><br /> Description : style de comparaison Unicode.<br /><br /> Options de tri utilisés pour le tri des données Unicode.|  
  
 Dans le jeu de propriétés DBPROPSET_SQLSERVERSTREAM spécifique au fournisseur, le pilote OLE DB pour SQL Server définit la propriété supplémentaire suivante.  
  
|ID de propriété|Description|  
|-----------------|-----------------|  
|SSPROP_STREAM_XMLROOT|Type : VT_BSTR R/W: Read/Write (Lecture/écriture)<br /><br /> Description : le résultat d'une requête FOR XML ne peut pas être un document bien formé. Lorsque cette propriété est spécifiée, le résultat d'une requête 'select … for XML' est encapsulée dans la balise racine fournie par la propriété pour retourner un document XML bien formé. Si la requête est exécutée dans le navigateur, il se peut que le navigateur affiche les erreurs de l'analyseur lors du chargement du résultat. Pour éviter l'erreur, SQL ISAPI prend en charge le mot clé ROOT. Ce mot clé est mappé avec la propriété SSPROP_STREAM_XMLROOT.|  
  
## <a name="see-also"></a> Voir aussi  
 [Objets Source de données &#40;OLE DB&#41;](../../oledb/ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
