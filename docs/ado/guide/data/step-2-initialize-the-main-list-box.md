---
title: "Étape 2 : Initialiser la zone de liste principale | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1454493-1c86-46c2-ada8-d3c6fcdaf3c1
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c291da043764d9599311704af86952eec47578b6
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="step-2-initialize-the-main-list-box"></a>Étape 2 : Initialiser la zone de liste principale
Pour déclarer les objets Record et Recordset globaux, insérez le code suivant dans (général) (déclarations) pour Form1 :  
  
```  
Option Explicit  
Dim grec As Record  
Dim grs As Recordset  
```  
  
 Ce code déclare des références d’objet global pour les objets d’enregistrement et le jeu d’enregistrements qui seront utilisés plus loin dans ce scénario.  
  
## <a name="to-connect-to-a-url-and-populate-lstmain"></a>Se connecter à une URL et remplir lstMain  
 Insérez le code suivant dans le Gestionnaire d’événements de chargement du formulaire pour Form1 :  
  
```  
Private Sub Form_Load()  
    Set grec = New Record  
    Set grs = New Recordset  
    grec.Open "", "URL=http://servername/foldername/", , _  
        adOpenIfExists Or adCreateCollection  
    Set grs = grec.GetChildren  
    While Not grs.EOF  
        lstMain.AddItem grs(0)  
        grs.MoveNext  
    Wend  
End Sub  
```  
  
 Ce code instancie les objets Record et Recordset globaux. L’objet Record, `grec`, est ouvert avec l’URL définie comme ActiveConnection. Si l’URL existe, il est ouvert ; Si elle n’existe pas déjà, il est créé. Notez que vous devez remplacer « http://servername/foldername/ » avec une URL valide à partir de votre environnement.  
  
 L’objet Recordset, `grs`, est ouvert sur les enfants de l’enregistrement, `grec`. Puis `lstMain` est remplie avec les noms de fichiers des ressources publiées à l’URL.  
  
## <a name="see-also"></a>Voir aussi  
 [Scénario de publication Internet](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Étape 1 : Configurer le projet Visual Basic](../../../ado/guide/data/step-1-set-up-the-visual-basic-project.md)   
 [Étape 3 : Remplir la zone de liste de champs](../../../ado/guide/data/step-3-populate-the-fields-list-box.md)

