---
title: Conditions d’implémentation des éléments de rapports personnalisés | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- custom report items
ms.assetid: cfacd816-00d6-4a3d-be72-1bba6f7f6886
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: dc2898fd9bca67b0b6838e685ad0cb7e2739e3c0
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56029810"
---
# <a name="custom-report-item-implementation-requirements"></a>Conditions d'implémentation des éléments de rapports personnalisés
  Cette rubrique examine les conditions préalables au développement et au déploiement d'éléments de rapports personnalisés.  
  
## <a name="development-and-deployment-requirements"></a>Conditions de développement et de déploiement  
 Le développement d’un élément de rapport personnalisé pour [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] requiert ce qui suit :  
  
-   Accès en tant qu’administrateur à un serveur exécutant [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
-   [!INCLUDE[vsprvsext](../../includes/vsprvsext-md.md)] ou version ultérieure avec le SDK [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] installé.  
  
-   Accès à la documentation du Kit de développement logiciel (SDK)  [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
-   Connaissance de la création de composants et des espaces de noms de modèles de composants dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Pour plus d'informations, consultez « Création de composants » et « Espace de noms de modèles de composants dans Visual Studio » sur msdn.microsoft.com.  
  
## <a name="language-and-namespace-requirements"></a>Conditions de langage et d'espace de noms  
 Les éléments de rapports personnalisés [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prennent entièrement en charge le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Vous pouvez développer des éléments de rapports personnalisés à l'aide du langage compatible .NET de votre choix.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] offre de nombreux outils et fonctionnalités au développeur pour simplifier et accélérer les cycles itératifs du codage, du débogage et du test et pour simplifier le déploiement. Le Kit de développement [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK inclut des compilateurs [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] et C# ainsi que des outils connexes.  
  
-   Les éléments de rapports personnalisés utilisent les espaces de noms `Microsoft.ReportDesigner` et <xref:Microsoft.ReportingServices.Interfaces>. Ceux-ci sont stockés dans les assemblys Microsoft.ReportingServices.Designer.DLL et Microsoft.ReportingServices.Interfaces.DLL, lesquels sont installés dans le cadre de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
-   Les composants intervenant au moment de la conception des éléments de rapports personnalisés doivent implémenter des interfaces à partir de l'espace de noms <xref:System.ComponentModel> dans le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. L'espace de noms <xref:System.ComponentModel> est décrit dans la documentation du Kit de développement [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK.  
  
> [!IMPORTANT]  
>  Le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] est installé par défaut avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mais pas le Kit de développement [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK. Les liens vers les rubriques relatives au Kit de développement figurant dans cette section ne fonctionnent que si le Kit de développement est installé sur l'ordinateur et que la documentation qui lui est propre figure dans la documentation en ligne. Après avoir installé le SDK [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], vous pouvez ajouter la documentation le concernant à la documentation en ligne et à la table des matières en suivant les instructions figurant dans [Ajouter ou supprimer la documentation du produit SQL Server](../../2014-toc/books-online-for-sql-server-2014.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un composant d’exécution d’éléments de rapport personnalisé](creating-a-custom-report-item-run-time-component.md)   
 [Création d’un composant au moment de la conception d’éléments de rapport personnalisé](creating-a-custom-report-item-design-time-component.md)   
 [Procédure : Déployer un élément de rapport personnalisé](how-to-deploy-a-custom-report-item.md)   
 [Bibliothèques de classes d'éléments de rapports personnalisés](custom-report-item-class-libraries.md)  
  
  
