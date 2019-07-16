---
title: Didacticiel RDS (VBScript) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- RDS tutorial [ADO], VBScript
ms.assetid: e2a48c4d-88b1-43ff-a202-9cdec54997d2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d45347bcdf212158fb6a0ee9f4599e1e1b00ff54
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67922426"
---
# <a name="rds-tutorial-vbscript"></a>Tutoriel RDS (VBScript)
Il s’agit du didacticiel RDS, écrites en Microsoft Visual Basic Scripting Edition. Pour obtenir une description de l’objectif de ce didacticiel, consultez le [didacticiel RDS](../../../ado/guide/remote-data-service/rds-tutorial.md).  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Dans ce didacticiel, [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) et [RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) sont créés au moment du design - autrement dit, ils sont définis avec des balises d’objet, comme suit : `<OBJECT>...</OBJECT>`. Vous pouvez également, ils pu être créés au moment de l’exécution avec le [CreateObject (méthode) (RDS)](../../../ado/reference/rds-api/createobject-method-rds.md) (méthode). Par exemple, le **RDS. DataControl** objet a pu être créé comme suit :  
  
```vb
Set DC = Server.CreateObject("RDS.DataControl")  
   <!-- RDS.DataControl -->  
   <OBJECT   
      ID="DC1" CLASSID="CLSID:BD96C556-65A3-11D0-983A-00C04FC29E33">  
   </OBJECT>  
  
   <!-- RDS.DataSpace -->  
   <OBJECT   
      ID="DS1" WIDTH=1 HEIGHT=1  
      CLASSID="CLSID:BD96C556-65A3-11D0-983A-00C04FC29E36">  
   </OBJECT>  
  
   <SCRIPT LANGUAGE="VBScript">  
  
   Sub RDSTutorial()  
   Dim DF1   
```  
  
## <a name="step-1---specify-a-server-program"></a>Étape 1 : spécifier un programme de serveur  
 VBScript peut découvrir le nom du serveur Web IIS, il s’exécute en accédant à VBScript **Request.ServerVariables** méthode disponible pour les Pages ASP :  
  
```vb
"https://<%=Request.ServerVariables("SERVER_NAME")%>"  
```  
  
 Toutefois, pour ce didacticiel, vous devez utiliser le serveur imaginaire, « yourServer ».  
  
> [!NOTE]
>  Faites attention au type de données de **ByRef** arguments. VBScript ne permet pas de spécifier le type de variable, vous devez donc toujours passer un **Variant**. Lorsque vous utilisez HTTP, RDS vous autorise à transmettre un type Variant à une méthode qui attend un type de données-non si vous l’appelez avec le **RDS. DataSpace** objet [CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md) (méthode). Lorsque vous utilisez DCOM ou un serveur in-process, vous devez faire correspondre les types de paramètres sur les côtés client et serveur, ou vous recevrez une erreur « Incompatibilité de Type ».  
  
```vb
Set DF1 = DS1.CreateObject("RDSServer.DataFactory", "https://yourServer")  
```  
  
## <a name="step-2a---invoke-the-server-program-with-rdsdatacontrol"></a>Étape 2 a : appeler le programme serveur avec RDS. DataControl  
 Cet exemple est simplement un commentaire illustrant le comportement par défaut de la **RDS. DataControl** consiste à effectuer la requête spécifiée.  
  
```vb
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="DC1">  
   <PARAM NAME="SQL" VALUE="SELECT * FROM Authors">  
   <PARAM NAME="Connect" VALUE="DSN=Pubs;">  
   <PARAM NAME="Server" VALUE="https://yourServer/">  
</OBJECT>  
...  
<SCRIPT LANGUAGE="VBScript">  
  
Sub RDSTutorial2A()  
   Dim RS  
   DC1.Refresh  
   Set RS = DC1.Recordset  
...  
```  
  
## <a name="step-2b---invoke-the-server-program-with-rdsserverdatafactory"></a>Étape 2 b : appeler le programme serveur avec RDSServer.DataFactory  
  
## <a name="step-3---server-obtains-a-recordset"></a>Étape 3 : le serveur obtient un objet Recordset  
  
## <a name="step-4---server-returns-the-recordset"></a>Étape 4 : serveurs retourne le jeu d’enregistrements  
  
```vb
Set RS = DF1.Query("DSN=Pubs;", "SELECT * FROM Authors")  
```  
  
## <a name="step-5---datacontrol-is-made-usable-by-visual-controls"></a>Étape 5 : DataControl devient utilisable par des contrôles visuels  
  
```vb
' Assign the returned recordset to the DataControl.  
  
DC1.SourceRecordset = RS  
```  
  
## <a name="step-6a---changes-are-sent-to-the-server-with-rdsdatacontrol"></a>Étape 6 a - les modifications sont envoyées au serveur avec RDS. DataControl  
 Cet exemple est simplement un commentaire illustrant comment la **RDS. DataControl** effectue des mises à jour.  
  
```vb
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="DC1">  
   <PARAM NAME="SQL" VALUE="SELECT * FROM Authors">  
   <PARAM NAME="Connect" VALUE="DSN=Pubs;">  
   <PARAM NAME="Server" VALUE="https://yourServer/">  
</OBJECT>  
...  
<SCRIPT LANGUAGE="VBScript">  
  
Sub RDSTutorial6A()  
Dim RS  
DC1.Refresh  
...  
Set RS = DC1.Recordset  
' Edit the Recordset object...  
' The SERVER and CONNECT properties are already set from Step 2A.  
Set DC1.SourceRecordset = RS  
...  
DC1.SubmitChanges  
```  
  
## <a name="step-6b---changes-are-sent-to-the-server-with-rdsserverdatafactory"></a>Étape 6 b - modifications sont envoyées au serveur avec RDSServer.DataFactory  
  
```vb
DF.SubmitChanges "DSN=Pubs", RS  
  
End Sub  
</SCRIPT>  
</BODY>  
</HTML>  
```  
  
 **Il s’agit de la fin du didacticiel.**  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel RDS](../../../ado/guide/remote-data-service/rds-tutorial.md)   
