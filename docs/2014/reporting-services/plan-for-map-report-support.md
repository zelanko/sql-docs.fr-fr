---
title: Planifier la prise en charge des rapports cartographiques | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ddc97a7-7ee5-475d-bc49-3b814dce7e19
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: df796e2dd4e132164f00716a9cb12f7b498d8984
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66108082"
---
# <a name="plan-for-map-report-support"></a>Planifier la prise en charge de rapport cartographique
  [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]prend en charge les rapports cartographiques qui utilisent des sources de données spatiales. Les données spatiales peuvent provenir de bases de données SQL Server, de fichiers de formes ESRI ou de la Bibliothèque de cartes installée avec Reporting Services ou le Générateur de rapports. Une carte peut également afficher un arrière-plan de mosaïques Bing. Un auteur de rapport peut créer un rapport qui spécifie des données spatiales ou des mosaïques Bing comme dynamique et récupéré au moment de l'exécution ou comme statique et incorporé dans la définition de rapport.  
  
## <a name="support-for-bing-maps"></a>Prise en charge de Bing Maps  
 Les cartes peuvent inclure une couche d'arrière-plan qui affiche des mosaïques Bing. Pour consulter un rapport publié qui a une couche de mosaïques, le serveur de rapports doit être configuré pour récupérer des mosaïques à partir des services Web Bing Maps. Pour plus d'informations, consultez [RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md).  
  
 Dans chaque rapport, les auteurs peuvent spécifier s'il faut utiliser une connexion SSL (Secure Sockets Layer) pour récupérer des mosaïques auprès du serveur de mosaïques. Pour ce faire, dans le volet Propriétés de la couche de mosaïques, ils doivent définir la propriété booléenne `true`UseSecureConnection sur.  
  
> [!NOTE]  
>  Pour plus d'informations sur l'utilisation de mosaïques Bing dans votre rapport, consultez [Conditions supplémentaires d'utilisation](https://go.microsoft.com/fwlink/?LinkId=151371) et [Déclaration de confidentialité](https://go.microsoft.com/fwlink/?LinkId=151372)(éventuellement en anglais).  
  
## <a name="report-design-recommendations"></a>Recommandations relatives à la conception des rapports  
 Une bonne conception pour les rapports cartographiques requiert que l'auteur de rapport évalue les compromis entre les données spatiales dynamiques et statiques et recherche un équilibre qui profite aux utilisateurs de rapport. Les éléments cartographiques incorporés peuvent augmenter considérablement la taille de la définition de rapport, mais ils réduisent le temps nécessaire pour afficher le rapport cartographique. Les éléments cartographiques dynamiques réduisent la taille de la définition de rapport, mais augmentent le temps requis pour traiter et afficher la carte. L'auteur de rapport doit rechercher l'équilibre correct entre ces différents facteurs.  
  
 Lorsque la taille de la définition de rapport est un problème, en tant qu'administrateur du serveur de rapports, vous pouvez encourager les concepteurs de rapports à réduire la quantité de données spatiales dans une définition de rapport.  
  
 Dans les conditions suivantes, les éléments cartographiques sont incorporés dans la définition de rapport :  
  
-   Lorsque le rapport est créé, la source de données spatiales est sur le système de fichiers local. Cela inclut des données spatiales de la bibliothèque de cartes ou de fichiers de forme ESRI installés localement. Par défaut, l'Assistant Carte et l'Assistant Couche incorporent les données spatiales à partir de sources de données sur le système de fichiers local.  
  
-   L'auteur de rapport choisit l'option pour incorporer manuellement des données spatiales dans le rapport.  
  
 Pour aider à réduire la taille des définitions de rapports qui ont des cartes, les auteurs de rapport peuvent utiliser une ou plusieurs des options suivantes :  
  
-   À partir du Concepteur de rapports dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], ajoutez des sources de données spatiales qui sont des fichiers de forme ESRI au projet de serveur de rapports. Lorsque vous déployez le projet, les fichiers de forme ESRI sont publiés sur le serveur de rapports en plus du rapport. Lorsque l'auteur de rapport exécute l'Assistant Carte, il peut spécifier une source de données spatiales du projet Report Server et les éléments cartographiques ne sont pas incorporés par défaut dans les définitions de rapport.  
  
-   À partir du Générateur de rapports, ajoutez des sources de données spatiales qui sont des fichiers de forme ESRI en sélectionnant des fichiers de forme du serveur de rapports. Lorsque l'auteur de rapport exécute l'Assistant Carte, il peut naviguer jusqu'à et sélectionner une source de données spatiales du serveur de rapports et les éléments cartographiques ne sont pas incorporés par défaut dans les définitions de rapport.  
  
-   Lorsque les données cartographiques doivent être incorporées, ajustez le centre de la fenêtre d'affichage et le niveau de zoom de façon à inclure uniquement les données cartographiques nécessaires pour le rapport.  
  
 Pour plus d’informations, [mappe &#40;générateur de rapports et les&#41;SSRS ](report-design/maps-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Résoudre les problèmes liés aux rapports : rapports cartographiques &#40;Générateur de rapports et SSRS&#41;](report-design/troubleshoot-reports-map-reports-report-builder-and-ssrs.md)  
  
  
