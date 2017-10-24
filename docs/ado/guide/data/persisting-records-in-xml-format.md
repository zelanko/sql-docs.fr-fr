---
title: "Maintien d’enregistrements au Format XML | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persisting data [ADO]
- data updates [ADO], persisting data
- data persistence [ADO]
- XML persistence [ADO]
- updating data [ADO], persisting data
ms.assetid: f3113ec4-ae31-428f-89c6-bc1024f128ea
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a45c434bdcf551e97eb97f85997ab73c883b599c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="persisting-records-in-xml-format"></a>Maintien d’enregistrements au Format XML
Comme le format ADTG, **Recordset** persistance au format XML est implémenté avec le fournisseur de persistance Microsoft OLE DB. Ce fournisseur génère un ensemble de lignes avant uniquement en lecture seule à partir d’un fichier XML ou un flux qui contient les informations de schéma générées par ADO enregistré. De même, elle peut prendre un ADO **Recordset**, générer un fichier XML et enregistrez-le dans un fichier ou tout objet qui implémente le modèle COM **IStream** interface. (En fait, un fichier est juste un autre exemple d’un objet qui prend en charge **IStream**.) Pour les versions 2.5 et ultérieures, ADO repose sur l’analyseur Microsoft XML (MSXML) pour charger le code XML dans le **Recordset**; par conséquent msxml.dll est obligatoire.  
  
> [!NOTE]
>  Certaines restrictions s’appliquent lors de l’enregistrement hiérarchique **jeux d’enregistrements** (formes de données) au format XML. Vous ne pouvez pas enregistrer au format XML si l’hiérarchique **Recordset** contient en attente de mises à jour, et vous ne pouvez pas enregistrer un paramétrable hiérarchique **Recordset**. Pour plus d’informations, consultez [filtré de persistance et de jeux d’enregistrements](../../../ado/guide/data/persisting-filtered-and-hierarchical-recordsets.md).  
  
 Le moyen le plus simple pour conserver les données au format XML et le recharger dans ADO est avec le **enregistrer** et **ouvrir** méthodes, respectivement. L’exemple de code ADO suivant illustre l’enregistrement des données dans le **titres** table dans un fichier nommé titles.sav.  
  
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
  
 ADO conserve toujours l’ensemble de **Recordset** objet. Si vous souhaitez conserver un sous-ensemble de lignes de la **Recordset** de l’objet, utilisez le **filtre** méthode pour restreindre les lignes ou de modifier la clause de sélection. Toutefois, vous devez ouvrir une **Recordset** objet avec un curseur côté client (**CursorLocation** = **adUseClient**) à utiliser le **defiltre** méthode pour enregistrer un sous-ensemble de lignes. Par exemple, pour extraire des titres qui commencent par la lettre « b », vous pouvez appliquer un filtre à open **Recordset** objet :  
  
```  
rs.Filter "title_id like 'B*'"  
rs.Save "btitles.sav", adPersistXML  
```  
  
 ADO utilise toujours l’ensemble de lignes du moteur de curseur Client pour produire un défilement signet **Recordset** objet par-dessus les données avant uniquement générées par le fournisseur de persistance.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Format de persistance XML](../../../ado/guide/data/xml-persistence-format.md)  
  
-   [Espaces de noms](../../../ado/guide/data/namespaces.md)  
  
-   [Section de schéma](../../../ado/guide/data/schema-section.md)  
  
-   [Section de données](../../../ado/guide/data/data-section.md)  
  
-   [Jeux d’enregistrements hiérarchiques dans XML](../../../ado/guide/data/hierarchical-recordsets-in-xml.md)  
  
-   [Propriétés dynamiques du jeu d’enregistrements au format XML](../../../ado/guide/data/recordset-dynamic-properties-in-xml.md)  
  
-   [Transformations XSLT](../../../ado/guide/data/xslt-transformations.md)  
  
-   [Enregistrement à l’objet DOM XML](../../../ado/guide/data/saving-to-the-xml-dom-object.md)  
  
-   [Considérations de sécurité XML](../../../ado/guide/data/xml-security-considerations.md)  
  
-   [Scénario de persistance des objets Recordset XML](../../../ado/guide/data/xml-recordset-persistence-scenario.md)

