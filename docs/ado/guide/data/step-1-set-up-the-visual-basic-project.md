---
title: 'Étape 1 : Configurer le projet Visual Basic | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 77d3bfa5-fc9f-4a72-93b4-790c7d227988
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ce9e337a1ea45db851bafd32e0af476ae33fd3c0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47798797"
---
# <a name="step-1-set-up-the-visual-basic-project"></a>Étape 1 : Configurer le projet Visual Basic
Dans ce scénario, il est supposé que vous avez Microsoft Visual Basic 6.0, ADO 2.5 ou version ultérieure et le fournisseur Microsoft OLE DB pour la publication Internet installé sur votre système. Vous commencez par créer un nouveau projet et puis ajouter des contrôles au formulaire par défaut dans le projet.  
  
### <a name="to-create-an-ado-project"></a>Pour créer un projet ADO :  
  
1.  Dans Microsoft Visual Basic, créez un nouveau projet EXE Standard.  
  
2.  Dans le menu projet, choisissez références.  
  
3.  Sélectionnez « Bibliothèque Microsoft ActiveX Data Objects 2.5 » et cliquez sur OK.  
  
### <a name="to-insert-controls-on-the-main-form"></a>Pour insérer des contrôles du formulaire principal :  
  
1.  Ajoutez un contrôle ListBox à Form1. Affectez à sa propriété de nom **lstMain**.  
  
2.  Ajoutez un autre contrôle ListBox à Form1. Affectez à sa propriété de nom **lstDetails**.  
  
3.  Ajoutez un contrôle TextBox à Form1. Affectez à sa propriété de nom **txtDetails**.  
  
## <a name="see-also"></a>Voir aussi  
 [Scénario de publication Internet](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Étape 2 : Initialiser la zone de liste principale](../../../ado/guide/data/step-2-initialize-the-main-list-box.md)
