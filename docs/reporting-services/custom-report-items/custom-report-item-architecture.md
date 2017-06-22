---
title: "Architecture d’élément de rapport personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom report items, architecture
ms.assetid: 2a88ea46-c9f8-4dd7-aad1-16de11da4f06
caps.latest.revision: 16
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 8b79071c67e3ada6fcfc0f588d9cba4580a981e8
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="custom-report-item-architecture"></a>Architecture des éléments de rapports personnalisés
  Un élément de rapport personnalisé est une extension au langage RDL (Report Definition Language) qui permet aux développeurs d'ajouter des fonctionnalités qui ne sont pas prises en charge en mode natif au langage RDL ou d'étendre les fonctionnalités de contrôles existants. Un élément de rapport personnalisé comprend deux composants principaux : le composant d'exécution et le composant de conception. Ces composants sont implémentés en tant qu'assemblys [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] et peuvent être écrits dans n'importe quel langage conforme CLS.  
  
## <a name="the-run-time-component"></a>Le composant d’exécution  
 Le composant d'exécution pour un élément de rapport personnalisé est appelé par le processeur de rapports au moment de l'exécution. Le composant d'exécution accepte les données passées par le processeur de rapports au moment de l'exécution, traite ces données, puis retourne une image contenant l'élément de rapport personnalisé rendu.  
  
 ![Composant d’exécution de rapport personnalisé élément](../../reporting-services/custom-report-items/media/customreportitemrun-timecomponentarchitecture.gif "composant runtime d’élément de rapport personnalisé")  
  
## <a name="the-design-time-component"></a>Composant de conception  
 Le composant de conception autorise la définition et la manipulation de l'élément de rapport personnalisé dans l'interface du Concepteur de rapports dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Le composant de conception comprend plusieurs sous-contrôles qui contrôlent l'apparence et les propriétés de l'élément de rapport personnalisé dans l'environnement de conception.  
  
 ![Composant de conception de rapport personnalisé élément](../../reporting-services/custom-report-items/media/customreportitemdesign-timecomponentarchitecture.gif "composant au moment du design d’élément de rapport personnalisé")  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un composant d’exécution de rapport personnalisé élément](../../reporting-services/custom-report-items/creating-a-custom-report-item-run-time-component.md)   
 [Création d’un composant au moment du Design d’élément rapport personnalisé](../../reporting-services/custom-report-items/creating-a-custom-report-item-design-time-component.md)   
 [Comment : déployer un élément de rapport personnalisé](../../reporting-services/custom-report-items/how-to-deploy-a-custom-report-item.md)  
  
  
