---
title: Plus d’informations sur la persistance des recordsets | Microsoft Docs
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
- updating data [ADO], persisting data
ms.assetid: a9b287f5-04b0-4514-8143-f67879ca9842
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3e626c924e7b84312877b47f811329e215f47e42
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47846857"
---
# <a name="more-about-recordset-persistence"></a>En savoir plus sur la persistance des recordsets
Prend en charge de l’objet ADO Recordset stockant le contenu d’un **Recordset** objet dans un fichier à l’aide de son [enregistrer](../../../ado/reference/ado-api/save-method.md) (méthode). Le fichier stocké de façon permanente peut-être exister sur un ordinateur local du lecteur, serveur, ou en tant qu’URL sur un serveur Web de site. Plus tard, le fichier peut être restauré avec une le [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) méthode de la **Recordset** objet ou le [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) méthode de la [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet.  
  
 En outre, le [GetString](../../../ado/reference/ado-api/getstring-method-ado.md) méthode convertit un **Recordset** objet à un formulaire dans lequel les lignes et colonnes sont délimitées par des caractères que vous spécifiez.  
  
 Pour conserver un **Recordset**, commencez par convertir dans un format qui peut être stocké dans un fichier. **Jeu d’enregistrements** objets peuvent être stockées dans le format Advanced Data TableGram (ADTG) propriétaire ou au langage XML (Extensible Markup) ouvert. Exemples ADTG sont présentés dans la section suivante. Pour plus d’informations sur la persistance XML, consultez [persistance des enregistrements au format XML](../../../ado/guide/data/persisting-records-in-xml-format.md).  
  
 Enregistrez les modifications en attente dans le fichier persistant. Cela vous permet d’émettre une requête qui retourne un **Recordset** (objet), les modifications le **Recordset**, enregistre ainsi que les modifications en attente, restaure le **Recordset**, puis met à jour la source de données avec les modifications en attente.  
  
 Pour plus d’informations sur le stockage de manière permanente **Stream** , consultez [flux et persistance](../../../ado/guide/data/streams-and-persistence.md).  
  
 Pour obtenir un exemple de **Recordset** persistance, voir le scénario de persistance XML Recordset.  
  
## <a name="example"></a>Exemple  
  
### <a name="save-a-recordset"></a>Enregistrer un jeu d’enregistrements :  
  
```  
Dim rs as New ADODB.Recordset  
rs.Save "c:\yourFile.adtg", adPersistADTG  
```  
  
### <a name="open-a-persisted-file-with-recordsetopen"></a>Ouvrez un fichier persistant avec Recordset.Open :  
  
```  
Dim rs as New ADODB.Recordset  
rs.Open "c:\yourFile.adtg", "Provider=MSPersist",,,adCmdFile  
```  
  
 Si vous le souhaitez, si le **Recordset** est ne disposez pas d’une connexion active, vous pouvez accepter les valeurs par défaut et le code suivant :  
  
```  
Dim rs as New ADODB.Recordset  
rs.Open "c:\yourFile.adtg"  
```  
  
### <a name="open-a-persisted-file-with-connectionexecute"></a>Ouvrez un fichier persistant avec Connection.Execute :  
  
```  
Dim conn as New ADODB.Connection  
Dim rs as ADODB.Recordset  
conn.Open "Provider=MSPersist"  
Set rs = conn.execute("c:\yourFile.adtg")  
```  
  
### <a name="open-a-persisted-file-with-rdsdatacontrol"></a>Ouvrez un fichier persistant avec RDS. DataControl :  
 Dans ce cas, le **Server** propriété n’est pas définie.  
  
```  
Dim dc as New RDS.DataControl  
dc.Connection = "Provider=MSPersist"  
dc.SQL = "c:\yourFile.adtg"  
dc.Refresh  
```  
  
## <a name="see-also"></a>Voir aussi  
 [GetString, méthode (ADO)](../../../ado/reference/ado-api/getstring-method-ado.md)   
 [Fournisseur de persistance Microsoft OLE DB (fournisseur de services ADO)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)   
 [Objet Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Flux et persistance](../../../ado/guide/data/streams-and-persistence.md)
