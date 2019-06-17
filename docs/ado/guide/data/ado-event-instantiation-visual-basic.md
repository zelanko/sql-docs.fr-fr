---
title: Instanciation des événements ADO Visual Basic | Microsoft Docs
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
manager: jroth
ms.openlocfilehash: 590a3c282492fd07a86eae1715ffc9b027764fac
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66702407"
---
# <a name="ado-event-instantiation-visual-basic"></a>Instanciation des événements ADO Visual Basic
Pour gérer des événements ADO dans Microsoft® Visual Basic®, vous devez déclarer une variable au niveau du module à l’aide du **WithEvents** mot clé. La variable peut être déclarée uniquement dans le cadre d’un module de classe et doit être déclarée au niveau du module. Ce n’est pas aussi restrictif qu’il y paraît, toutefois, étant donné que Visual Basic **formulaire** objets sont également des classes. Le plus simple pour gérer les événements ADO consiste à déclarer une variable à l’aide **WithEvents**. L’exemple suivant gère la **ConnectComplete** événement pour un **connexion** objet :  
  
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
  
 Le **connexion** objet est déclaré au niveau du **formulaire** niveau à l’aide de la **WithEvents** mot clé pour activer la gestion des événements. Le Gestionnaire d’événements Form_Load crée l’objet en affectant une nouvelle **connexion** objet *connEvent* , puis ouvre la connexion. Bien sûr, une application réelle feriez d’un traitement supplémentaire dans le Gestionnaire d’événements Form_Load est est présenté ici.
