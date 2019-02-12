---
title: Lier un rapport à un modèle en tant que rapport généré interactif | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- customizing clickthrough reports
- clickthrough reports, customizing
- clickthrough reports, templates
ms.assetid: 3af42de3-67ef-41c2-bc8a-7045baec6f63
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 7d0ec49168e4a23a019eb91fc708e286bf0e1ac4
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56037040"
---
# <a name="link-a-report-to-a-model-as-a-clickthrough-report"></a>Lier un rapport à un modèle en tant que rapport généré interactif
  Plutôt que d'utiliser les modèles de rapports générés interactifs à l'aide de clics, vous pouvez créer un rapport de Générateur de rapports et le lier à une entité spécifique dans le modèle de rapport. Lorsque la personne qui affiche le rapport clique sur des données interactives dans le rapport principal, ce rapport s'affiche sous forme de rapport consultable à l'aide de clics. Pour lier un rapport à une entité, utilisez le Gestionnaire de rapports [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
> [!IMPORTANT]  
>  L'entité principale, ou de base, qui est utilisée dans le rapport doit être celle à laquelle le rapport est lié.  
  
### <a name="to-start-report-manager-from-a-browser"></a>Pour démarrer le Gestionnaire de rapports à partir du navigateur  
  
1.  Ouvrez [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer 6.0 ou version ultérieure.  
  
2.  Dans la barre d'adresses du navigateur Web, tapez l'URL du Gestionnaire de rapports. Par défaut, l’URL est http://\<*ComputerName*> / reports.  
  
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
  
  
