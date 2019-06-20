---
title: Persistance des enregistrements au Format XML | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- XML persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: f3113ec4-ae31-428f-89c6-bc1024f128ea
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 783dfb43f1eaebcc823f49000f589542465b1735
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66701935"
---
# <a name="persisting-records-in-xml-format"></a>Persistance des enregistrements au format XML
Comme le format ADTG, **Recordset** persistance au format XML est implémentée avec le fournisseur Microsoft OLE DB de persistance. Ce fournisseur génère un ensemble de lignes avant uniquement et en lecture seule à partir d’un fichier XML ou un flux qui contient les informations de schéma générées par ADO enregistré. De même, il peut prendre un ADO **Recordset**, générer du code XML et enregistrez-le dans un fichier ou de tout objet qui implémente le modèle COM **IStream** interface. (En fait, un fichier est juste un autre exemple d’un objet qui prend en charge **IStream**.) Pour les versions 2.5 et versions ultérieures, ADO repose sur Microsoft XML Parser (MSXML) pour charger le code XML dans le **Recordset**; par conséquent msxml.dll est requise.  
  
> [!NOTE]
>  Certaines limitations s’appliquent lors de l’enregistrement hiérarchique **Recordsets** (formes de données) au format XML. Vous ne pouvez pas enregistrer au format XML si l’hiérarchique **Recordset** contient en attente de mises à jour, et vous ne pouvez pas enregistrer un paramétrable hiérarchique **Recordset**. Pour plus d’informations, consultez [filtré de persistance et de jeux d’enregistrements](../../../ado/guide/data/persisting-filtered-and-hierarchical-recordsets.md).  
  
 Le moyen le plus simple pour conserver les données au format XML et recharger dans ADO est avec la **enregistrer** et **Open** méthodes, respectivement. L’exemple de code ADO suivant illustre l’enregistrement des données dans le **titres** table dans un fichier nommé titles.sav.  
  
```  
Dim rs as new Recordset  
Dim rs2 as new Recordset  
Dim c as new Connection  
Dim s as new Stream  
  
' Query the Titles table.  
c.Open "provider=sqloledb;data source=MySQLServer;initial catalog=pubs;Integrated Security='SSPI'"  
rs.cursorlocation = adUseClient  
rs.Open "select * from titles", c, adOpenStatic  
  
' Save to the file in the XML format. Note that if you don't specify   
' adPersistXML, a binary format (ADTG) will be used by default.  
rs.Save "titles.sav", adPersistXML  
  
' Save the recordset into the ADO Stream object.  
rs.save s, adPersistXML  
rs.Close  
c.Close  
  
set rs = nothing  
  
' Reopen the file.  
rs.Open "titles.sav",,,,adCmdFile  
' Open the Stream back into a Recordset.  
rs2.open s  
```  
  
 ADO conserve toujours l’intégralité de **Recordset** objet. Si vous souhaitez conserver un sous-ensemble de lignes de la **Recordset** de l’objet, utilisez le **filtre** méthode pour cibler les lignes ou de modifier la clause de sélection. Toutefois, vous devez ouvrir une **Recordset** objet avec un curseur côté client (**CursorLocation** = **adUseClient**) à utiliser le **filtrer** méthode pour enregistrer un sous-ensemble de lignes. Par exemple, pour extraire des titres qui commencent par la lettre « b », vous pouvez appliquer un filtre à une ouverture **Recordset** objet :  
  
```  
rs.Filter "title_id like 'B*'"  
rs.Save "btitles.sav", adPersistXML  
```  
  
 ADO utilise toujours l’ensemble de lignes du moteur de curseur Client pour générer un défilement signet **Recordset** objet par-dessus les données avant uniquement générées par le fournisseur de persistance.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Format de persistance XML](../../../ado/guide/data/xml-persistence-format.md)  
  
-   [Espaces de noms](../../../ado/guide/data/namespaces.md)  
  
-   [Section de schéma](../../../ado/guide/data/schema-section.md)  
  
-   [Section de données](../../../ado/guide/data/data-section.md)  
  
-   [Recordsets hiérarchiques dans XML](../../../ado/guide/data/hierarchical-recordsets-in-xml.md)  
  
-   [Propriétés dynamiques du recordset dans XML](../../../ado/guide/data/recordset-dynamic-properties-in-xml.md)  
  
-   [Transformations XSLT](../../../ado/guide/data/xslt-transformations.md)  
  
-   [Enregistrement dans l’objet DOM XML](../../../ado/guide/data/saving-to-the-xml-dom-object.md)  
  
-   [Considérations relatives à la sécurité de XML](../../../ado/guide/data/xml-security-considerations.md)  
  
-   [Scénario de persistance des recordsets XML](../../../ado/guide/data/xml-recordset-persistence-scenario.md)
