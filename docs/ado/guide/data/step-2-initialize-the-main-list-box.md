---
title: 'Étape 2 : initialiser la zone de liste principale | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: a1454493-1c86-46c2-ada8-d3c6fcdaf3c1
author: rothja
ms.author: jroth
ms.openlocfilehash: c6aaf4d87e4e01e6f32e1d681d93e5a2291c3999
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760815"
---
# <a name="step-2-initialize-the-main-list-box"></a>Étape 2 : Initialiser la zone de liste principale
Pour déclarer des objets record et Recordset globaux, insérez le code suivant dans le (général) (déclarations) de Form1 :  
  
```  
Option Explicit  
Dim grec As Record  
Dim grs As Recordset  
```  
  
 Ce code déclare des références d’objet globales pour les objets record et Recordset qui seront utilisés ultérieurement dans ce scénario.  
  
## <a name="to-connect-to-a-url-and-populate-lstmain"></a>Pour vous connecter à une URL et remplir lstMain  
 Insérez le code suivant dans le gestionnaire d’événements de chargement de formulaire pour Form1 :  
  
```  
Private Sub Form_Load()  
    Set grec = New Record  
    Set grs = New Recordset  
    grec.Open "", "URL=https://servername/foldername/", , _  
        adOpenIfExists Or adCreateCollection  
    Set grs = grec.GetChildren  
    While Not grs.EOF  
        lstMain.AddItem grs(0)  
        grs.MoveNext  
    Wend  
End Sub  
```  
  
 Ce code instancie les objets record et Recordset globaux. L’objet record, `grec` , est ouvert avec une URL spécifiée comme ActiveConnection. Si l’URL existe, elle est ouverte ; s’il n’existe pas déjà, il est créé. Notez que vous devez remplacer « <https://servername/foldername/> » par une URL valide de votre environnement.  
  
 L’objet Recordset, `grs` , est ouvert sur les enfants de l’enregistrement, `grec` . `lstMain`Est ensuite renseigné avec les noms de fichiers des ressources publiées sur l’URL.  
  
## <a name="see-also"></a>Voir aussi  
 [Scénario de publication Internet](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Étape 1 : configurer le projet Visual Basic](../../../ado/guide/data/step-1-set-up-the-visual-basic-project.md)   
 [Étape 3 : Remplir la zone de liste des champs](../../../ado/guide/data/step-3-populate-the-fields-list-box.md)
