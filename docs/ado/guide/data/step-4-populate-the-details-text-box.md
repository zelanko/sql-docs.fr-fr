---
title: 'Étape 4 : Remplir la zone de texte Détails | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: cb4273e2-c907-4a86-a621-3bf110088228
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 060de551afa266dae4d5384fe765e16b997bcccd
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53206648"
---
# <a name="step-4-populate-the-details-text-box"></a>Étape 4 : Remplir la zone de texte Détails
Pour remplir la zone de texte de détails, créez une nouvelle sous-routine nommée **recFields** et insérez le code suivant :  
  
```  
Sub recFields(r As Record, l As ListBox, t As TextBox)  
    Dim f As Field  
    Dim s As Stream  
    Set s = New Stream  
    Dim str As String  
  
    For Each f In r.Fields  
        l.AddItem f.Name & ": " & f.Value  
    Next  
    t.Text = ""  
    If r!RESOURCE_CONTENTCLASS = "text/plain" Then  
        s.Open r, adModeRead, adOpenStreamFromRecord  
        str = s.ReadText(1)  
        s.Position = 0  
        If Asc(Mid(str, 1, 1)) = 63 Then '//63 = "?"  
            s.Charset = "ascii"  
            s.Type = adTypeText  
        End If  
        t.Text = s.ReadText(adReadAll)  
    End If  
End Sub  
```  
  
 Ce code remplit `lstDetails` avec les champs et les valeurs de l’enregistrement simple transmis à `recFields`. Si la ressource est un fichier texte, un Stream de texte est ouvert à partir de l’enregistrement de ressource. Le code détermine si le jeu de caractères est ASCII et copie le contenu de Stream dans `txtDetails`.  
  
## <a name="see-also"></a>Voir aussi  
 [Scénario de publication Internet](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Étape 3 : Remplir la zone de liste de champs](../../../ado/guide/data/step-3-populate-the-fields-list-box.md)
