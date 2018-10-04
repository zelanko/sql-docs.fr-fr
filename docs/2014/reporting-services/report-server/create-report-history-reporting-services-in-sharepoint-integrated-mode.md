---
title: Créer un historique de rapport (Reporting Services en mode intégré SharePoint) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report history [Reporting Services], SharePoint
ms.assetid: e57ec746-05ae-4ff6-8e39-6cde87310daa
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 7420b28bcdf12b0e173b097396972d3cc53ef973
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48176589"
---
# <a name="create-report-history-reporting-services-in-sharepoint-integrated-mode"></a>Créer un historique de rapport (Reporting Services en mode intégré SharePoint)
  L'historique de rapport est un ensemble d'instantanés de rapport que vous créez au fil du temps. Chaque instantané est une copie du rapport tel qu'il existait lors de sa création. Il inclut la mise en page et les données en vigueur dans le rapport lors de la création de l'instantané. Les informations de rendu ne sont pas stockées avec l'instantané. Lorsque vous ouvrez un instantané dans l'historique de rapport, elle s'affiche au format HTML dans le composant WebPart Visionneuse de rapports. Une fois son rendu effectué, vous pouvez l'exporter vers d'autres formats d'application.  
  
 Pour créer un historique de rapport, le rapport doit être capable de s'exécuter sans assistance (c'est-à-dire que le serveur de rapports doit être capable d'exécuter le rapport sans intervention de l'utilisateur). Vous devez disposer de l'autorisation Modifier les éléments sur la bibliothèque qui contient le rapport. Pour afficher ou supprimer l'historique de rapport, vous devez posséder l'autorisation Afficher les versions ou Supprimer les versions.  
  
### <a name="to-create-a-snapshot-or-report-history-on-demand"></a>Pour créer un historique des instantanés et des rapports à la demande  
  
1.  Pointez sur le rapport.  
  
2.  Cliquez pour afficher la flèche orientée vers le bas, puis sélectionnez **Afficher l’historique du rapport**.  
  
3.  Cliquez sur **Nouvel instantané**. Si le bouton n'est pas visible, cela signifie que vous n'êtes pas autorisé à créer des instantanés dans l'historique de rapport.  
  
4.  Pour afficher l'instantané que vous venez de créer, sélectionnez-le dans la liste. Chaque instantané est identifié par un horodatage qui indique sa date et son heure de création. Vous ne pouvez pas renommer l'instantané, le déplacer ni le modifier.  
  
### <a name="to-schedule-report-history"></a>Pour planifier un historique de rapport  
  
1.  Pointez sur le rapport.  
  
2.  Cliquez pour afficher la flèche orientée vers le bas, puis sélectionnez **Gérer les options de traitement**.  
  
3.  Dans **Options des instantanés d’historique**, cliquez sur **Créer des instantanés d’historique de rapport dans une planification**.  
  
4.  Si vous disposez d’une planification partagée qui contient les informations de planification à utiliser, cliquez sur **Suivant une planification partagée** , puis sélectionnez la planification appropriée. Sinon, cliquez sur **Suivant une planification personnalisée**, puis sur **Configurer** , afin de spécifier les options de création d’un historique de rapport selon une planification périodique.  
  
### <a name="to-create-report-history-when-data-is-refreshed-in-a-report"></a>Pour créer un historique de rapport lorsque les données sont actualisées dans un rapport  
  
1.  Pointez sur le rapport.  
  
2.  Cliquez pour afficher la flèche orientée vers le bas, puis sélectionnez **Gérer les options de traitement**.  
  
3.  Dans **Options des instantanés d’historique**, cliquez sur **Stocker tous les instantanés de données de rapports dans l’historique de rapport**.  
  
## <a name="see-also"></a>Voir aussi  
 [Définir les options de traitement &#40;Reporting Services en mode intégré SharePoint&#41;](../set-processing-options-reporting-services-in-sharepoint-integrated-mode.md)  
  
  
