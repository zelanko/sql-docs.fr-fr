---
title: 'Instanciation des événements ADO : Visual Basic | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
ms.assetid: dce0a2a3-326f-4aaf-a822-6c5549833afa
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ead713a37d4ecf8bdfecd0d6c485684d1ad0777f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67926079"
---
# <a name="ado-event-instantiation-visual-basic"></a>Instanciation des événements ADO Visual Basic
Pour gérer les événements ADO dans Microsoft® Visual Basic®, vous devez déclarer une variable au niveau du module à l’aide du mot clé **WithEvents** . La variable ne peut être déclarée que dans le cadre d’un module de classe et doit être déclarée au niveau du module. Cela n’est cependant pas aussi restrictif, car les objets de **formulaire** Visual Basic sont également des classes. La façon la plus simple de gérer les événements ADO consiste à déclarer une variable à l’aide de **WithEvents**. L’exemple suivant gère l’événement **ConnectComplete** pour un objet **Connection** :  
  
```  
' BeginEventExampleVB02  
Dim WithEvents connEvent As Connection  
Attribute connEvent.VB_VarHelpID = -1  
  
Private Sub Form_Load()  
Dim strConn As String  
  
   ' Create a new object with event  
   ' handling enabled.  
   strConn = "Provider=sqloledb;" & _  
      "Data Source=MyServer;" & _  
      "Initial Catalog=Northwind;" & _  
      "Integrated Security=SSPI;"  
   Set connEvent = New ADODB.Connection  
   connEvent.Open strConn  
End Sub  
  
Private Sub connEvent_ConnectComplete(ByVal pError As ADODB.Error, _  
    adStatus As ADODB.EventStatusEnum, _  
    ByVal pConnection As ADODB.Connection)  
Dim strMsg As String  
  
   If adStatus = adStatusErrorsOccurred Then  
      Select Case pError.Number  
         Case adErrOperationCancelled  
            ' The operation was cancelled in the  
            ' Will event. Notify the user and exit.  
            strMsg = "I'm sorry you can't connect right now." & vbCrLf  
            strMsg = strMsg & "Click OK to exit."  
            Unload Me  
         Case Else  
            strMsg = "Error " & Format(pError.Number) & vbCrLf  
            strMsg = strMsg & pError.Description  
            strMsg = strMsg & "Click OK to exit."  
            Unload Me  
      End Select  
   End If  
   frmWait.btnOK.Enabled = True  
End Sub  
' EndEventExampleVB02  
```  
  
 L’objet de **connexion** est déclaré au niveau du **formulaire** à l’aide du mot clé **WithEvents** pour activer la gestion des événements. Le gestionnaire d’événements Form_Load crée en fait l’objet en assignant un nouvel objet de **connexion** à *connEvent* , puis ouvre la connexion. Bien entendu, une application réelle effectue un traitement plus grand dans le gestionnaire d’événements Form_Load que ce qui est indiqué ici.
