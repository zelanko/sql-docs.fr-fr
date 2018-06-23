---
title: Lier un rapport à un modèle en tant qu’un rapport généré interactif | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- customizing clickthrough reports
- clickthrough reports, customizing
- clickthrough reports, templates
ms.assetid: 3af42de3-67ef-41c2-bc8a-7045baec6f63
caps.latest.revision: 26
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 9dfe16933e0c2b335cf68816113c336561aac1ac
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36144208"
---
# <a name="link-a-report-to-a-model-as-a-clickthrough-report"></a>Lier un rapport à un modèle en tant que rapport généré interactif
  Plutôt que d'utiliser les modèles de rapports générés interactifs à l'aide de clics, vous pouvez créer un rapport de Générateur de rapports et le lier à une entité spécifique dans le modèle de rapport. Lorsque la personne qui affiche le rapport clique sur des données interactives dans le rapport principal, ce rapport s'affiche sous forme de rapport consultable à l'aide de clics. Pour lier un rapport à une entité, utilisez [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] le Gestionnaire de rapports.  
  
> [!IMPORTANT]  
>  L'entité principale, ou de base, qui est utilisée dans le rapport doit être celle à laquelle le rapport est lié.  
  
### <a name="to-start-report-manager-from-a-browser"></a>Pour démarrer le Gestionnaire de rapports à partir du navigateur  
  
1.  Ouvrez [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer 6.0 ou version ultérieure.  
  
2.  Dans la barre d'adresses du navigateur Web, tapez l'URL du Gestionnaire de rapports. Par défaut, l’URL est http://\<*Nom_Ordinateur*> / reports.  
  
### <a name="to-create-a-customized-clickthrough-report"></a>Pour créer un rapport consultable à l'aide de clics  
  
1.  Accédez au modèle de rapport auquel vous souhaitez ajouter le rapport généré interactif personnalisé.  
  
2.  Double-cliquez sur le modèle de rapport.  
  
3.  Cliquez sur **Rapports générés interactifs**.  
  
4.  Sélectionnez l'entité à laquelle vous souhaitez attacher le rapport généré interactif personnalisé.  
  
    > [!NOTE]  
    >  Cette entité doit être la même que l'entité de base du rapport généré interactif personnalisé.  
  
5.  Pour afficher le rapport personnalisé après avoir cliqué sur une seule instance de l'entité sélectionnée, cliquez sur le bouton **Parcourir** du rapport à une seule instance.  
  
     -ou-  
  
     Pour afficher le rapport personnalisé après avoir cliqué sur plusieurs instances de l'entité sélectionnée, cliquez sur le bouton **Parcourir** du rapport à plusieurs instances.  
  
6.  Sélectionnez le rapport, puis cliquez sur **OK**.  
  
7.  Cliquez sur **Appliquer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Rapports générés interactifs &#40;SSRS&#41;](reports/clickthrough-reports-ssrs.md)  
  
  