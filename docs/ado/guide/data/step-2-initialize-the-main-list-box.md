---
title: 'Étape 2 : Initialiser la zone de liste principale | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: a1454493-1c86-46c2-ada8-d3c6fcdaf3c1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8ad89d806f8a6774cb0fe2de056e30fd274a517c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67924085"
---
# <a name="step-2-initialize-the-main-list-box"></a>Étape 2 : Initialiser la zone de liste principale
Pour déclarer des objets globaux d’enregistrement et le jeu d’enregistrements, insérez le code suivant dans (général) (déclarations) pour Form1 :  
  
```  
Option Explicit  
Dim grec As Record  
Dim grs As Recordset  
```  
  
 Ce code déclare des références d’objet global pour les objets d’enregistrement et le jeu d’enregistrements qui seront utilisés plus loin dans ce scénario.  
  
## <a name="to-connect-to-a-url-and-populate-lstmain"></a>Pour vous connecter à une URL et remplir lstMain  
 Insérez le code suivant dans le Gestionnaire d’événements Form Load pour Form1 :  
  
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
  
 Ce code instancie les objets globaux de l’enregistrement et le jeu d’enregistrements. L’objet Record, `grec`, est ouvert avec une URL spécifiée comme ActiveConnection. Si l’URL existe, il est ouvert ; Si elle n’existe pas déjà, il est créé. Notez que vous devez remplacer «<https://servername/foldername/>» avec une URL valide à partir de votre environnement.  
  
 L’objet Recordset, `grs`, est ouvert sur les enfants de l’enregistrement, `grec`. Puis `lstMain` est rempli avec les noms de fichier des ressources publiées à l’URL.  
  
## <a name="see-also"></a>Voir aussi  
 [Scénario de publication Internet](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Étape 1 : Configurer le projet Visual Basic](../../../ado/guide/data/step-1-set-up-the-visual-basic-project.md)   
 [Étape 3 : Remplir la zone de liste de champs](../../../ado/guide/data/step-3-populate-the-fields-list-box.md)
