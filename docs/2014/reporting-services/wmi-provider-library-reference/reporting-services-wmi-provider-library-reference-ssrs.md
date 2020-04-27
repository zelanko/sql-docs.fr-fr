---
title: Référence de bibliothèque du fournisseur WMI de Reporting Services (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- Reporting Services WMI Provider Library
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- WMI provider [Reporting Services], library
ms.assetid: 17ba711d-7eff-4423-9168-63dc425a3428
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2a98ca22f9d34627e484a698dcf540b31808d07e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66097023"
---
# <a name="reporting-services-wmi-provider-library-reference-ssrs"></a>Référence de bibliothèque du fournisseur WMI de Reporting Services (SSRS)
  Le fournisseur [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Windows Management Instrumentation (WMI) prend en charge des opérations WMI qui vous permettent d’écrire des scripts et du code pour modifier des paramètres du serveur de rapports et du Gestionnaire de rapports.  
  
 Par exemple, si vous voulez spécifier que la sécurité intégrée est utilisée quand le serveur de rapports se connecte à la base de données du serveur de rapports, créez une instance de la classe MSReportServer_ConfigurationSetting et utilisez la propriété DatabaseIntegratedSecurity de l’instance de serveur de rapports. Les classes répertoriées dans le tableau suivant représentent des composants [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Les classes sont définies dans l’espace de noms [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)] ou [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)] . Chacune des classes prend en charge des opérations en lecture et en écriture. Les opérations de création ne sont pas prises en charge.  
  
## <a name="classes"></a>Classes  
 [classe MSReportServer_Instance](msreportserver-instance-class.md)  
 Fournit les informations de base nécessaires à un client pour établir la connexion à un serveur de rapports installé.  
  
 [Classe MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
 Représente les paramètres d'installation et d'exécution d'une instance de serveur de rapports. Ces paramètres sont stockés dans le fichier de configuration du serveur de rapports.  
  
 Pour plus d’informations sur les opérations WMI, consultez la documentation du SDK WMI [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] inclus dans le kit de développement logiciel (SDK).  
  
## <a name="see-also"></a>Voir aussi  
 [Accéder au fournisseur WMI Reporting Services](../tools/access-the-reporting-services-wmi-provider.md)   
 [Informations techniques de référence &#40;SSRS&#41;](../technical-reference-ssrs.md)  
  
  
