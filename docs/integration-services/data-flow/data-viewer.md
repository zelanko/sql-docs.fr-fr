---
title: Visionneuse de données | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: data-flow
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql13.dts.designer.dataviewer.f1
helpviewer_keywords:
- Data Viewer dialog box
ms.assetid: 6351309a-688f-4e82-9697-1712130f10a1
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6566c459be7b1e1fb128befacc471129c2dcfcc2
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="data-viewer"></a>Visionneuse de données
  Si un chemin d'accès est configuré pour utiliser une visionneuse de données, la visionneuse affiche les données tampon par tampon à mesure qu'elles se déplacent entre deux composants de flux de données.  
  
## <a name="options"></a>Options  
 **Flèche verte**  
 Cliquez sur cette option pour afficher les données du tampon suivant. Si les données peuvent être déplacées dans un tampon unique, cette option n'est pas disponible.  
  
 **Détacher**  
 Détachez la visionneuse de données.  
  
 **Remarque** Le détachement d'une visionneuse de données ne la supprime pas. Si la visionneuse de données est détachée, les données continuent de circuler sur le chemin mais les données de la visionneuse ne sont pas mises à jour pour refléter les données de chaque tampon.  
  
 **Attacher**  
 Attachez une visionneuse de données.  
  
 **Remarque** Lorsque la visionneuse de données est attachée, elle affiche les informations de chaque tampon du flux de données, puis s'arrête. Vous pouvez progresser dans les tampons à l'aide de la flèche verte.  
  
 **Copier les données**  
 Copiez les données du tampon actuel dans le Presse-papiers.  
  
## <a name="see-also"></a> Voir aussi  
 [Débogage d’un flux de données](../../integration-services/troubleshooting/debugging-data-flow.md)  
  
  
