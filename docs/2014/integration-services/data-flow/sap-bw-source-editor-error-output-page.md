---
title: Éditeur de source SAP BW (page Sortie d’erreur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b6e23b0c-949a-46d1-8424-4dc3d9035e79
author: janinezhang
ms.author: janinez
ms.openlocfilehash: c3c94fead420fcd20978d662f2849369018af50e
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84914319"
---
# <a name="sap-bw-source-editor-error-output-page"></a>Éditeur de source SAP BW (page Sortie d'erreur)
  Utilisez la page **Sortie d'erreur** de l' **Éditeur de source SAP BW** pour sélectionner les options de gestion des erreurs et pour définir les propriétés des colonnes de sortie d'erreur.  
  
 Pour en savoir plus sur le composant source SAP BW de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 pour SAP BW, consultez [SAP BW Source](sap-bw-source.md).  
  
> [!IMPORTANT]  
>  La documentation de Microsoft Connector 1.1 pour SAP BW suppose que vous êtes familiarisé avec l'environnement SAP Netweaver BW. Pour plus d'informations sur SAP Netweaver BW, ou sur la configuration des objets et des processus SAP Netweaver BW objets, consultez la documentation SAP.  
  
> [!IMPORTANT]  
>  Vous devez disposer d'une licence SAP supplémentaire pour extraire des données à partir de SAP Netweaver BW. Vérifiez auprès de SAP.  
  
 **Pour ouvrir la page Sortie d'erreur**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui contient la source SAP BW.  
  
2.  Sous l’onglet **Flux de données** , double-cliquez sur la source SAP BW.  
  
3.  Dans l' **Éditeur de source SAP BW**, cliquez sur **Sortie d'erreur** pour ouvrir la page **Sortie d'erreur** de l'éditeur.  
  
## <a name="options"></a>Options  
  
> [!NOTE]  
>  Si vous ne connaissez pas toutes les valeurs requises pour configurer la source, adressez-vous à votre administrateur SAP.  
  
 **Entrée ou Sortie**  
 Affichez le nom de la source de données.  
  
 **Colonne**  
 Affichez les colonnes externes (source) que vous avez sélectionnées dans la page **Colonnes** de la boîte de dialogue **Éditeur de source SAP BW** . Pour plus d’informations sur cette boîte de dialogue, consultez [Éditeur de source SAP BW &#40;page Colonnes&#41;](sap-bw-source-editor-columns-page.md).  
  
 **Error**  
 Spécifiez ce que le composant source SAP BW doit faire en cas d'erreur : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
 **Troncation**  
 Spécifiez ce que le composant source SAP BW doit faire en cas de troncation : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
 **Description**  
 Affiche la description de l'erreur.  
  
 **Définir cette valeur sur les cellules sélectionnées**  
 Spécifiez ce que le composant source SAP BW doit faire pour l'ensemble des cellules sélectionnées lorsqu'une erreur ou une troncation se produit : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
 **Appliquer**  
 Appliquez l'option de gestion des erreurs aux cellules sélectionnées.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de source SAP BW &#40;page Gestionnaire de connexions&#41;](sap-bw-source-editor-connection-manager-page.md)   
 [Éditeur de source SAP BW &#40;page Colonnes&#41;](sap-bw-source-editor-columns-page.md)   
 [Éditeur de source SAP BW &#40;page Avancé&#41;](sap-bw-source-editor-advanced-page.md)   
 [Aide (F1) sur Microsoft Connector 1.1 pour SAP BW](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
