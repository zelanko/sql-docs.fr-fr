---
title: 'Étape 4 : remplir la zone de texte détails | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: cb4273e2-c907-4a86-a621-3bf110088228
author: rothja
ms.author: jroth
ms.openlocfilehash: 2110384afa66e74e17d4e3c9a8600b5825cc412e
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760785"
---
# <a name="step-4-populate-the-details-text-box"></a>Étape 4 : Remplir la zone de texte Détails
Pour remplir la zone de texte détails, créez une sous-routine nommée **recFields** et insérez le code suivant :  
  
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
  
 Ce code est rempli `lstDetails` avec les champs et les valeurs de l’enregistrement simple passé à `recFields` . Si la ressource est un fichier texte, un flux de texte est ouvert à partir de l’enregistrement de ressource. Le code détermine si le jeu de caractères est ASCII et copie le contenu du flux dans `txtDetails` .  
  
## <a name="see-also"></a>Voir aussi  
 [Scénario de publication Internet](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Étape 3 : Remplir la zone de liste des champs](../../../ado/guide/data/step-3-populate-the-fields-list-box.md)
