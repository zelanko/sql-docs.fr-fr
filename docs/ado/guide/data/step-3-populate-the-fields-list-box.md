---
title: 'Étape 3 : Remplir la zone de liste de champs | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 315c32dc-aeb1-4629-b30e-87b44e8f84d1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1aecb94fd7367b12ed2c1aaca06ffe26f586e604
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53206888"
---
# <a name="step-3-populate-the-fields-list-box"></a>Étape 3 : Remplir la zone de liste de champs
Pour remplir la zone de liste de champs, insérez le code suivant dans le Gestionnaire d’événements Click de `lstMain`:  
  
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
  
 Ce code déclare et instancie les objets d’enregistrement et le jeu d’enregistrements locales, `rec` et `rs`, respectivement.  
  
 La ligne correspondant à la ressource sélectionnée dans `lstMain` est effectuée à la ligne actuelle de `grs`. Puis la zone de liste de détails est désactivée et `rec` est ouvert avec la ligne actuelle de `grs` comme source.  
  
 Si la ressource est un enregistrement de la collection, tel que spécifié par [RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md), le jeu d’enregistrements local `rs` est ouvert sur les enfants de rec. Puis `lstDetails` est rempli avec les valeurs des lignes de `rs`.  
  
 Si la ressource est un enregistrement simple, `recFields` est appelée. Pour plus d’informations sur `recFields`, consultez l’étape suivante.  
  
 Aucun code n’est implémenté si la ressource est un document structuré.  
  
## <a name="see-also"></a>Voir aussi  
 [Scénario de publication Internet](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Étape 2 : Initialiser la zone de liste principale](../../../ado/guide/data/step-2-initialize-the-main-list-box.md)   
 [Étape 4 : Remplir la zone de texte Détails](../../../ado/guide/data/step-4-populate-the-details-text-box.md)
