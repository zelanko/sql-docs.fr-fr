---
title: Éditeur de destination SAP BW (page Sortie d’erreur) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a543d811-0bd2-4890-a0d3-f5fdcd4524b8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fc348bdd4ddbd5380987994691ec462a248f7a4b
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85431316"
---
# <a name="sap-bw-destination-editor-error-output-page"></a>Éditeur de destination SAP BW (page Sortie d'erreur)
  Utilisez la page **Sortie d’erreur** de **l’Éditeur de destination SAP BW** pour définir les options de gestion des erreurs.  
  
 Pour en savoir plus sur la destination SAP BW de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 pour SAP BW, consultez [Destination SAP BW](sap-bw-destination.md).  
  
> [!IMPORTANT]  
>  La documentation de Microsoft Connector 1.1 pour SAP BW suppose que vous êtes familiarisé avec l'environnement SAP Netweaver BW. Pour plus d'informations sur SAP Netweaver BW, ou sur la configuration des objets et des processus SAP Netweaver BW objets, consultez la documentation SAP.  
  
 **Pour ouvrir la page Sortie d'erreur**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui contient la destination SAP BW.  
  
2.  Sous l’onglet **Flux de données** , double-cliquez sur la destination SAP BW.  
  
3.  Dans **l’Éditeur de destination SAP BW**, cliquez sur **Sortie d’erreur** pour ouvrir la page **Sortie d’erreur** de l’éditeur.  
  
## <a name="options"></a>Options  
  
> [!NOTE]  
>  Si vous ne connaissez pas toutes les valeurs requises pour configurer la destination, adressez-vous à votre administrateur SAP.  
  
 **Entrée ou Sortie**  
 Affichez le nom de l'entrée.  
  
 **Colonne**  
 Cette option n'est pas utilisée.  
  
 **Error**  
 Spécifiez ce que la destination doit faire en cas d'erreur : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
 **Troncation**  
 Cette option n'est pas utilisée.  
  
 **Description**  
 Affichez la description de l'opération.  
  
 **Définir cette valeur sur les cellules sélectionnées**  
 Spécifiez ce que la destination doit faire pour l'ensemble des cellules sélectionnées lorsqu'une erreur ou une troncation se produit : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
 **Appliquer**  
 Appliquez l'option de gestion des erreurs aux cellules sélectionnées.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de destination SAP BW &#40;page Gestionnaire de connexions&#41;](sap-bw-destination-editor-connection-manager-page.md)   
 [Éditeur de destination SAP BW &#40;page Mappages&#41;](sap-bw-destination-editor-mappings-page.md)   
 [Éditeur de destination SAP BW &#40;page Avancé&#41;](sap-bw-destination-editor-advanced-page.md)   
 [Aide (F1) sur Microsoft Connector 1.1 pour SAP BW](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
