---
title: Boîte de dialogue Valider | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.ssis.ssms.ispackagevalidate.f1
- sql12.ssis.ssms.isprojectvalidate.f1
ms.assetid: 134e14ce-4f8d-4a20-889a-918014c841d8
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 4b426080f2c76e8abc4bcaff26d2d5f0d53bfcc0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36144558"
---
# <a name="validate-dialog-box"></a>Boîte de dialogue Valider
  Utilisez la boîte de dialogue **Valider** pour examiner les problèmes usuels d'un projet ou package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 En cas de problème, un message s'affiche en haut de la boîte de dialogue. Sinon, le terme Prêt s'affiche en haut.  
  
 **Que voulez-vous faire ?**  
  
-   [Ouvrir la boîte de dialogue Valider](#open_dialog)  
  
-   [Définir les options sur la page Général](#general)  
  
##  <a name="open_dialog"></a> Ouvrir la boîte de dialogue Valider  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous au serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
     Vous vous connectez à l'instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] qui héberge la base de données SSISDB.  
  
2.  Dans l'Explorateur d'objets, développez l'arborescence pour afficher le nœud **Integration Services Catalogues** .  
  
3.  Développez le nœud **SSISDB** .  
  
4.  Développez le dossier qui contient le projet ou package à valider.  
  
5.  Cliquez avec le bouton droit sur le projet ou le package, puis cliquez sur **Valider**.  
  
##  <a name="general"></a> Définir les options sur la page Général  
 **Environnement**  
 Sélectionnez l'environnement à utiliser pour valider le projet ou le package.  
  
 **Runtime 32 bits**  
 Sélectionnez cette option afin d'utiliser un runtime 32 bits pour exécuter un package.  
  
 L'onglet **Paramètres** indique les valeurs de paramètres que vous utilisez pour valider le projet ou le package. Voici les options de l'onglet Paramètres.  
  
 **Conteneur**  
 Indique l'objet qui contient le paramètre.  
  
 **Paramètre**  
 Indique le nom des paramètres.  
  
 **Value**  
 Indique la valeur du paramètre.  
  
 L'onglet **Gestionnaires de connexions** indique les valeurs de propriétés du gestionnaire de connexions que vous utilisez pour valider le projet ou le package.  
  
 Voici les options de l'onglet **Gestionnaires de connexions** .  
  
 **Conteneur**  
 Indique l'objet qui contient le gestionnaire de connexions.  
  
 **Nom**  
 Indique le nom du gestionnaire de connexions.  
  
 **Nom de la propriété**  
 Indique le nom de la propriété du gestionnaire de connexions.  
  
 **Value**  
 Indique la valeur affectée à la propriété du gestionnaire de connexions.  
  
  