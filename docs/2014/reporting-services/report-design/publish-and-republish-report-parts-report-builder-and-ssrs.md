---
title: Publier et republier des parties de rapports (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92dce484-f39b-403c-9caf-d8772bc3aca3
caps.latest.revision: 6
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 28c5f5063aa7e1c6e6fabe68405eb08a31feaad4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051422"
---
# <a name="publish-and-republish-report-parts-report-builder-and-ssrs"></a>Publier et republier des parties de rapports (Générateur de rapports et SSRS)
  Vous pouvez publier une partie de rapport avec des paramètres par défaut à un emplacement par défaut, ou vous pouvez modifier des métadonnées de partie de rapport, telles que le nom et la description, puis les enregistrer ailleurs sur un serveur de rapports. Vous pouvez également les enregistrer sur un site SharePoint intégré avec un serveur de rapports si vous avez les autorisations appropriées.  
  
 Vous pouvez publier uniquement la partie de rapport, avec le dataset duquel elle dépend incorporé, ou vous pouvez publier le dataset séparément. Si vous publiez le dataset séparément, il devient un dataset partagé et la partie de rapport est liée à celui-ci. Pour plus d’informations, consultez [Parties de rapports et datasets dans le Générateur de rapports](../report-data/report-parts-and-datasets-in-report-builder.md).  
  
 Vous pouvez republier une partie de rapport existante. Si vous avez les autorisations, vous pouvez enregistrer sur l'instance d'origine de la partie de rapport sur le serveur, même si vous ne l'avez pas créée. Vous pouvez également la publier comme une nouvelle partie de rapport et l'enregistrer au même emplacement ou à un endroit différent.  
  
### <a name="to-publish-a-report-part"></a>Pour publier une partie de rapport  
  
1.  Dans le menu du Générateur de rapports, cliquez sur **Publier les parties de rapport**.  
  
     Si vous n'êtes pas connecté à un serveur de rapports, vous serez invité à le faire. Si vous ne pouvez pas vous connecter à un serveur de rapports, vous ne pouvez pas publier des parties de rapport.  
  
2.  Pour enregistrer vos parties de rapport avec les paramètres par défaut à l’emplacement par défaut, cliquez sur **Publier toutes les parties de rapport avec les paramètres par défaut**.  
  
     Sinon, cliquez sur **Vérifier et modifier les parties de rapport avant de procéder à la publication**.  
  
3.  Modifiez le nom et la description de la partie de rapport : double-cliquez sur le nom pour le modifier et cliquez dans le champ **Description** pour ajouter une description.  
  
    > [!NOTE]  
    >  Il est judicieux de donner un nom et une description à la partie de rapport pour aider les personnes à l'identifier lors de la recherche. La longueur maximale du nom d'une partie de rapport est de 260 caractères pour le chemin d'accès entier, y compris les noms des dossiers sur le serveur, suivi par le nom réel de la partie de rapport.  
  
4.  Pour enregistrer votre partie de rapport dans un dossier autre que celui par défaut, cliquez sur le bouton **Parcourir** .  
  
5.  Quand vous avez défini les options pour toutes les parties de rapports du rapport, cliquez sur **Publier**.  
  
     Une fois que vous avez publié les parties de rapports, la boîte de dialogue affiche ceux qui ont été correctement publiés et ceux qui ne l'ont pas été. Vous pouvez consulter les détails dans la boîte de dialogue **Publier les parties de rapports** pour les parties de rapports dont la publication a échoué.  
  
6.  Cliquez sur **Fermer**.  
  
### <a name="to-republish-a-report-part"></a>Pour republier une partie de rapport  
  
1.  Suivez la procédure précédente pour la publication d'une partie de rapport.  
  
2.  Dans la boîte de dialogue **Publier les parties de rapport** , si vous cliquez sur **Publier en tant que nouvelle copie de la partie de rapport**, le Générateur de rapports n’enregistre pas sur la partie de rapport existante sur le serveur, mais crée à la place une autre partie de rapport.  
  
> [!NOTE]  
>  Si vous la publiez en tant que nouvelle partie de rapport, elle aura un nouvel ID unique. Elle ne recevra plus les mises à jour si la partie de rapport d'origine est modifiée.  
  
## <a name="see-also"></a>Voir aussi  
 [Parties de rapport &#40;rapport Générateur et SSRS&#41;](../report-parts-report-builder-and-ssrs.md)   
 [Parties de rapports et jeux de données dans le Générateur de rapports](../report-data/report-parts-and-datasets-in-report-builder.md)   
 [Résoudre les problèmes de parties de rapport &#40;rapport Générateur et SSRS&#41;](../troubleshoot-report-parts-report-builder-and-ssrs.md)   
 [Recherchez les mises à jour ou désactiver les mises à jour &#40;rapport Générateur et SSRS&#41;](../check-for-updates-or-turn-updates-off-report-builder-and-ssrs.md)   
 [Rechercher des parties de rapports et définir un dossier par défaut &#40;rapport Générateur et SSRS&#41;](browse-for-report-parts-and-set-a-default-folder-report-builder-and-ssrs.md)  
  
  