---
title: "&#201;diteur de source SAP BW (page Sortie d&#39;erreur) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.sapbwsource.erroroutput.f1"
ms.assetid: b6e23b0c-949a-46d1-8424-4dc3d9035e79
caps.latest.revision: 10
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 10
---
# &#201;diteur de source SAP BW (page Sortie d&#39;erreur)
  Utilisez la page **Sortie d'erreur** de l' **Éditeur de source SAP BW** pour sélectionner les options de gestion des erreurs et pour définir les propriétés des colonnes de sortie d'erreur.  
  
 Pour en savoir plus sur le composant source SAP BW de [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 pour SAP BW, consultez [Source SAP BW](../../integration-services/data-flow/sap-bw-source.md).  
  
> [!IMPORTANT]  
>  La documentation de Microsoft Connector 1.1 pour SAP BW suppose que vous êtes familiarisé avec l'environnement SAP Netweaver BW. Pour plus d'informations sur SAP Netweaver BW, ou sur la configuration des objets et des processus SAP Netweaver BW objets, consultez la documentation SAP.  
  
> [!IMPORTANT]  
>  Vous devez disposer d'une licence SAP supplémentaire pour extraire des données à partir de SAP Netweaver BW. Vérifiez auprès de SAP.  
  
 **Pour ouvrir la page Sortie d'erreur**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui contient la source SAP BW.  
  
2.  Sous l’onglet **Flux de données**, double-cliquez sur la source SAP BW.  
  
3.  Dans l' **Éditeur de source SAP BW**, cliquez sur **Sortie d'erreur** pour ouvrir la page **Sortie d'erreur** de l'éditeur.  
  
## Options  
  
> [!NOTE]  
>  Si vous ne connaissez pas toutes les valeurs requises pour configurer la source, adressez-vous à votre administrateur SAP.  
  
 **Entrée ou Sortie**  
 Affichez le nom de la source de données.  
  
 **Colonne**  
 Affichez les colonnes externes (source) que vous avez sélectionnées dans la page **Colonnes** de la boîte de dialogue **Éditeur de source SAP BW**. Pour plus d’informations sur cette boîte de dialogue, consultez [Éditeur de source SAP BW &#40;page Colonnes&#41;](../../integration-services/data-flow/sap-bw-source-editor-columns-page.md).  
  
 **Erreur**  
 Spécifiez ce que le composant source SAP BW doit faire en cas d'erreur : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
 **Troncation**  
 Spécifiez ce que le composant source SAP BW doit faire en cas de troncation : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
 **Description**  
 Affiche la description de l'erreur.  
  
 **Définir cette valeur sur les cellules sélectionnées**  
 Spécifiez ce que le composant source SAP BW doit faire pour l'ensemble des cellules sélectionnées lorsqu'une erreur ou une troncation se produit : ignorer l'échec, rediriger la ligne ou faire échouer le composant.  
  
 **Appliquer**  
 Appliquez l'option de gestion des erreurs aux cellules sélectionnées.  
  
## Voir aussi  
 [Éditeur de source SAP BW &#40;page Gestionnaire de connexions&#41;](../../integration-services/data-flow/sap-bw-source-editor-connection-manager-page.md)   
 [Éditeur de source SAP BW &#40;page Colonnes&#41;](../../integration-services/data-flow/sap-bw-source-editor-columns-page.md)   
 [Éditeur de source SAP BW &#40;page Avancé&#41;](../../integration-services/data-flow/sap-bw-source-editor-advanced-page.md)   
 [Aide (F1) sur Microsoft Connector 1.1 pour SAP BW](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  