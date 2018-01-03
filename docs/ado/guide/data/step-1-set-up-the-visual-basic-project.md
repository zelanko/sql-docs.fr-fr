---
title: "Étape 1 : Configurer le projet Visual Basic | Documents Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77d3bfa5-fc9f-4a72-93b4-790c7d227988
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 22dc4636b248be498317edccfb89f13b235ab525
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="step-1-set-up-the-visual-basic-project"></a>Étape 1 : Configurer le projet Visual Basic
Dans ce scénario, il est supposé que vous disposez de Microsoft Visual Basic 6.0, ADO 2.5 ou version ultérieure et le fournisseur Microsoft OLE DB pour la publication Internet installés sur votre système. Votre sera tout d’abord créer un nouveau projet, puis ajouter des contrôles au formulaire par défaut dans le projet.  
  
### <a name="to-create-an-ado-project"></a>Pour créer un projet ADO :  
  
1.  Dans Microsoft Visual Basic, créez un nouveau projet EXE Standard.  
  
2.  Dans le menu projet, choisissez références.  
  
3.  Sélectionnez « Microsoft ActiveX Data Objects 2.5 Library » et cliquez sur OK.  
  
### <a name="to-insert-controls-on-the-main-form"></a>Pour insérer des contrôles du formulaire principal :  
  
1.  Ajoutez un contrôle ListBox à Form1. Affectez à sa propriété de nom **lstMain**.  
  
2.  Ajoutez un autre contrôle ListBox à Form1. Affectez à sa propriété de nom **lstDetails**.  
  
3.  Ajoutez un contrôle TextBox à Form1. Affectez à sa propriété de nom **txtDetails**.  
  
## <a name="see-also"></a>Voir aussi  
 [Scénario de publication Internet](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Étape 2 : Initialiser la zone de liste principale](../../../ado/guide/data/step-2-initialize-the-main-list-box.md)
