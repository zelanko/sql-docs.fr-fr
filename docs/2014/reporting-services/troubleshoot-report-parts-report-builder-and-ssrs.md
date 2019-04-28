---
title: Résoudre les problèmes de parties de rapports (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: d9fe1932-46e7-421b-a8a9-4c54d9576e94
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3e677d9923315acc27c2b2d96d5d4eddf2ba8b51
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62855966"
---
# <a name="troubleshoot-report-parts-report-builder-and-ssrs"></a>Résoudre les problèmes liés aux parties de rapports (Générateur de rapports et SSRS)
  Ces conseils peuvent vous être utiles lors de l'utilisation de parties de rapports.  
  
## <a name="why-do-my-co-worker-and-i-see-different-instances-of-the-same-report-part-when-we-search-for-it"></a>Pourquoi est-ce que mon collègue et moi-même voyons des instances différentes de la même partie de rapport lorsque nous la recherchons ?  
 Il peut exister plusieurs instances d'une même partie de rapport sur un serveur de rapports ou site SharePoint intégré à un serveur de rapports, toutes avec le même identificateur global unique (GUID). Seule l'instance la plus récente est affichée dans la liste de résultats de la recherche. Dans certains cas, différentes instances d'une même partie de rapport peuvent avoir des autorisations différentes. Si votre collègue et vous-même avez des autorisations différentes sur le serveur, vous ne verrez pas la même instance. Par exemple, disons que plusieurs copies d'une partie de rapport, toutes avec le même GUID, sont enregistrées dans des dossiers différents sur un serveur de rapports en mode intégré SharePoint. Si les dossiers ont des autorisations différentes, les parties de rapport dans ces dossiers auront également des autorisations différentes.  
  
 Pour connaître les autorisations dont vous et votre collègue disposez, demandez à l'administrateur du serveur de rapports.  
  
## <a name="when-i-search-for-report-parts-that-i-uploaded-to-a-sharepoint-server-i-do-not-see-them-why-not"></a>Lorsque je recherche des parties de rapport que j'ai téléchargées sur un serveur SharePoint, je ne les voie pas. Pourquoi pas ?  
 Les parties de rapport que vous avez téléchargées manuellement dans une bibliothèque de documents SharePoint, au lieu de les publier à l'aide du Générateur de rapports, peuvent ne pas s'afficher dans la bibliothèque de parties de rapport. Il est possible que le serveur de rapports utilisé pour la recherche de bibliothèque doive être synchronisé avec le contenu de la bibliothèque de documents SharePoint. Pour plus d’informations, consultez [activer la fonctionnalité de synchronisation de fichier de serveur de rapports dans Administration centrale de SharePoint](../../2014/reporting-services/activate-report-server-file-sync-feature-sharepoint-central-administration.md) dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [la documentation en ligne](https://go.microsoft.com/fwlink/?LinkId=154888) sur msdn.microsoft.com.  
  
## <a name="why-cant-others-see-the-image-in-their-reports"></a>Pourquoi est-ce que d'autres personnes ne peuvent pas voir l'image dans leurs rapports ?  
 Si vous publiez une partie de rapport qui est un lien vers un fichier image, la partie de rapport est en fait juste un lien. Si d'autres personnes ne peuvent pas voir l'image lorsqu'elles ajoutent la partie de rapport d'image à leurs rapports, c'est peut-être parce qu'elles ne disposent pas d'autorisations pour l'image associée au lien.  
  
 Il existe quelques solutions pour remédier à ce problème :  
  
-   Faites du fichier image une partie de rapport, plutôt que de créer un lien vers le fichier image.  
  
-   Déplacez le fichier image vers un emplacement pour lequel d'autres personnes disposent d'autorisations.  
  
-   Demandez à l'administrateur du serveur de rapports de modifier les autorisations.  
  
## <a name="why-do-i-get-a-circular-reference-error-message-when-i-try-to-publish-my-report-part"></a>Pourquoi est-ce que j'obtiens un message d'erreur de « référence circulaire » lorsque j'essaie de publier ma partie de rapport ?  
 Si des éléments de rapport ont une référence circulaire, vous ne serez pas en mesure de les publier comme parties de rapport. Par exemple, un élément de rapport pointe sur un dataset, qui pointe ensuite sur un paramètre. Le paramètre, à son tour, pointe aussi sur le dataset. Vous devrez d'abord supprimer l'une des références avant de pouvoir publier la partie de rapport.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication de parties de rapports &#40;Générateur de rapports et SSRS&#41;](report-parts-report-builder-and-ssrs.md)  
  
  
