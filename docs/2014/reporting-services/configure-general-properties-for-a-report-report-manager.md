---
title: Configurer les propriétés générales d’un rapport (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], properties
- properties [Reporting Services], general
ms.assetid: 10b941b2-28e6-4408-9ee4-acebc63c8496
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 23184e77efbe41eae3d4de434a30ff8f3a4847ff
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "78177029"
---
# <a name="configure-general-properties-for-a-report-report-manager"></a>Configurer les propriétés générales d'un rapport (Gestionnaire de rapports)
  
### <a name="to-configure-general-report-properties"></a>Pour configurer les propriétés générales d'un rapport

1.  Démarrez le [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md).

2.  Dans Gestionnaire de rapports, accédez à la page **contenu** . Localisez le rapport pour lequel vous voulez configurer les propriétés générales et ouvrez-le.

3.  Cliquez sur l'onglet **Propriétés**.

     Ou, si la page **contenu** est en mode Détails, cliquez sur l’icône de la page de propriétés :

     ![Icône de la page de propriétés](media/prop.gif "Icône de la page de propriétés")

4.  La page Propriétés **générales** s’affiche et vous pouvez configurer les propriétés comme suit :

    -   Dans la section **Propriétés** , vous pouvez modifier le nom et la description du rapport.

    -   Vous pouvez activer la case à cocher **Masquer en mode liste** pour masquer l’élément lorsque la page est ouverte dans la mise en page par défaut (mode liste) qui réorganise les éléments sur la page.

    -   Dans la section **définition de rapport** , cliquez sur **modifier** pour extraire une copie de la définition de rapport. Les modifications que vous apportez localement à la définition de rapport ne sont pas enregistrées sur le serveur de rapports.

         Ou, pour mettre à jour la définition de rapport à partir d’un fichier. rdl, cliquez sur **mettre à jour**.

        > [!NOTE]
        >  Si vous procédez à la mise à jour d'une définition de rapport, redéfinissez les paramètres de la source de données une fois cette opération terminée.

    -   Utilisez les boutons **supprimer** ou **déplacer** pour supprimer ou déplacer le rapport.

    -   Vous pouvez également créer un rapport lié.

5.  Lorsque vous avez terminé de configurer les propriétés générales du rapport, cliquez sur **appliquer**.

## <a name="see-also"></a>Voir aussi
 [Déplacer ou supprimer un élément &#40;gestionnaire de rapports](report-server/move-or-delete-an-item-report-manager.md) [page&#41;contenu &#40;gestionnaire de rapports](../../2014/reporting-services/contents-page-report-manager.md)&#41;la [recherche, l’affichage et la gestion des rapports &#40;](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) [page Propriétés générales](../../2014/reporting-services/general-properties-page-reports-report-manager.md) générateur de rapports et SSRS &#41;, rapports &#40;gestionnaire de rapports&#41;


