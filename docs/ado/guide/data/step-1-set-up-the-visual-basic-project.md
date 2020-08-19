---
description: 'Étape 1 : Configurer le projet Visual Basic'
title: 'Étape 1 : configurer le projet de Visual Basic | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 77d3bfa5-fc9f-4a72-93b4-790c7d227988
author: rothja
ms.author: jroth
ms.openlocfilehash: d168a136d4cc80999591f0e36cb65abefa9c6c79
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452811"
---
# <a name="step-1-set-up-the-visual-basic-project"></a>Étape 1 : Configurer le projet Visual Basic
Dans ce scénario, il est supposé que vous avez Microsoft Visual Basic 6,0, ADO 2,5 ou version ultérieure et le fournisseur Microsoft OLE DB pour la publication Internet installée sur votre système. Vous allez d’abord créer un nouveau projet, puis ajouter des contrôles au formulaire par défaut dans le projet.  
  
### <a name="to-create-an-ado-project"></a>Pour créer un projet ADO :  
  
1.  Dans Microsoft Visual Basic, créez un projet EXE standard.  
  
2.  Dans le menu projet, choisissez références.  
  
3.  Sélectionnez « Microsoft ActiveX Data Objects bibliothèque 2,5 », puis cliquez sur OK.  
  
### <a name="to-insert-controls-on-the-main-form"></a>Pour insérer des contrôles sur le formulaire principal :  
  
1.  Ajoutez un contrôle ListBox à Form1. Affectez à sa propriété Name la valeur **lstMain**.  
  
2.  Ajoutez un autre contrôle ListBox à Form1. Affectez à sa propriété Name la valeur **lstDetails**.  
  
3.  Ajoutez un contrôle TextBox à Form1. Affectez à sa propriété Name la valeur **txtDetails**.  
  
## <a name="see-also"></a>Voir aussi  
 [Scénario de publication Internet](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Étape 2 : Initialiser la zone de liste principale](../../../ado/guide/data/step-2-initialize-the-main-list-box.md)
