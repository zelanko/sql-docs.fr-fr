---
title: Générateur (Assistant Rapport) de requêtes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.dataview.vdtquerydesigner.f1
- sql12.rtp.rptwizard.querybuilder.f1
helpviewer_keywords:
- Query Builder [Reporting Services]
ms.assetid: 1b0904ea-28c1-448e-b56c-c0fdfbc8b222
author: maggiesmsft
ms.author: maghan
manager: kfile
ms.openlocfilehash: 6f6a7e4e8e6d4a70ecb3695819f3648c86034b4e
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56013161"
---
# <a name="query-builder-report-wizard"></a>Générateur de requêtes (Assistant Rapport)
  Utilisez le générateur de requêtes pour spécifier une requête qui extrait un jeu de résultats à utiliser dans un rapport. Vous pouvez choisir l'un des deux générateurs de requêtes suivants :  
  
-   Le générateur de requêtes textuel (par défaut) fournit un espace de travail simple permettant de spécifier une requête et d'afficher les résultats. Vous pouvez spécifier plusieurs instructions [!INCLUDE[tsql](../includes/tsql-md.md)] , une syntaxe de requête ou de commande pour les extensions pour le traitement des données personnalisées et des requêtes spécifiées en tant qu'expressions. Comme le générateur de requêtes générique n'effectue pas de prétraitement de la requête et peut accepter toute sorte de syntaxe de requête, il représente l'outil par défaut du Concepteur de rapports.  
  
-   Le générateur de requêtes graphique propose une expérience visuelle plus riche. Il est utilisé dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] et dans d’autres parties de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Vous pouvez utiliser le générateur de requêtes graphique si vous ne créez pas d'expressions ou d'instructions SQL en plusieurs parties.  
  
     Pour basculer vers le générateur de requêtes graphique, actionnez le bouton bascule **Modifier en tant que texte** en haut à gauche de la fenêtre.  
  
 Vous pouvez également importer une requête à partir d'un autre rapport.  
  
## <a name="query-builder-options"></a>Options du générateur de requêtes  
 **Modifier en tant que texte**  
 Bascule entre le concepteur de requêtes textuel et le concepteur de requêtes graphique, si les deux sont utilisables pour la requête.  
  
 **Importer**  
 Ouvre la boîte de dialogue **Importer une requête** et affiche les fichiers .rdl et .sql de tous les rapports disponibles. Vous pouvez utiliser la requête importée telle quelle ou vous pouvez la modifier dans le générateur de requêtes.  
  
 **\! (Exécuter)**  
 Exécute la requête et retourne un jeu de résultats si la requête est valide. Notez que si la requête est une expression, vous ne pouvez pas l'exécuter. Pour vérifier une requête basée sur une expression, vous devez afficher un aperçu du rapport.  
  
 **Type de commande**  
 Spécifie le type Text, StoredProcedure ou TableDirect. La disponibilité d'un type de commande dépend de l'extension pour le traitement des données spécifiée.  
  
 **Volet de requête**  
 Tapez la requête  
  
 **Volet résultats**  
 Affiche le jeu de résultats retourné par la requête.  
  
## <a name="see-also"></a>Voir aussi  
 [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Aide de l’Assistant Rapport](../../2014/reporting-services/report-wizard-help.md)  
  
  
