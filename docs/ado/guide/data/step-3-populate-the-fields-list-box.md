---
description: 'Étape 3 : Remplir la zone de liste des champs'
title: 'Étape 3 : remplir la zone de liste Champs | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 315c32dc-aeb1-4629-b30e-87b44e8f84d1
author: rothja
ms.author: jroth
ms.openlocfilehash: d3a7378cfdce29094f5ae4271b9fe7bff7516753
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452791"
---
# <a name="step-3-populate-the-fields-list-box"></a>Étape 3 : Remplir la zone de liste des champs
Pour remplir la zone de liste champs, insérez le code suivant dans le gestionnaire d’événements Click de `lstMain` :  
  
```  
Private Sub lstMain_Click()  
    Dim rec As Record  
    Dim rs As Recordset  
    Set rec = New Record  
    Set rs = New Recordset  
    grs.MoveFirst  
    grs.Move lstMain.ListIndex  
    lstDetails.Clear  
    rec.Open grs  
    Select Case rec.RecordType  
        Case adCollectionRecord:  
            Set rs = rec.GetChildren  
            While Not rs.EOF  
                lstDetails.AddItem rs(0)  
                rs.MoveNext  
            Wend  
        Case adSimpleRecord:  
            recFields rec, lstDetails, txtDetails  
  
        Case adStructDoc:  
    End Select  
  
End Sub  
```  
  
 Ce code déclare et instancie les objets enregistrement et Recordset locaux, `rec` et `rs` , respectivement.  
  
 La ligne correspondant à la ressource sélectionnée dans `lstMain` est devenue la ligne actuelle de `grs` . La zone de liste détails est alors effacée et `rec` ouverte avec la ligne actuelle de `grs` comme source.  
  
 Si la ressource est un enregistrement de collection, tel que spécifié par [RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md), le Recordset local `rs` est ouvert sur les enfants de Rec. Ensuite, `lstDetails` est rempli avec les valeurs des lignes de `rs` .  
  
 Si la ressource est un enregistrement simple, `recFields` est appelée. Pour plus d’informations sur `recFields` , consultez l’étape suivante.  
  
 Aucun code n’est implémenté si la ressource est un document structuré.  
  
## <a name="see-also"></a>Voir aussi  
 [Scénario de publication Internet](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Étape 2 : initialiser la zone de liste principale](../../../ado/guide/data/step-2-initialize-the-main-list-box.md)   
 [Étape 4 : Remplir la zone de texte Détails](../../../ado/guide/data/step-4-populate-the-details-text-box.md)
