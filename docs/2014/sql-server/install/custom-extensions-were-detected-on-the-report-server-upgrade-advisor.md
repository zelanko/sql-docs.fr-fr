---
title: Des extensions personnalisées ont été détectées sur le serveur de rapports (conseiller de mise à niveau) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- rendering extensions [Reporting Services], custom extensions
- security extensions [Reporting Services]
- custom extensions [Reporting Services]
- data processing extensions [Reporting Services], custom extensions
- delivery extensions [Reporting Services]
ms.assetid: fa184bd7-11d6-4ea3-9249-bc1b13db49e5
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 2149e0434c13ccc9e284385999cf94c98fb937fa
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059379"
---
# <a name="custom-extensions-were-detected-on-the-report-server-upgrade-advisor"></a>Des extensions personnalisées ont été détectées sur le serveur de rapports (Conseiller de mise à niveau)
  Le Conseiller de mise à niveau a détecté des paramètres d'extension personnalisés dans les fichiers de configuration, ce qui indique que votre installation inclut une ou plusieurs extensions personnalisées pour le traitement des données, la remise, le rendu, la sécurité ou l'authentification. La mise à niveau déplacera les paramètres de configuration d'extension avec le serveur de rapports mis à niveau. Toutefois, si les extensions personnalisées sont installées dans le dossier installation du serveur de rapports existant, les fichiers d'assembly pour ces extensions personnalisées ne seront pas déplacés vers le nouveau dossier d'installation pendant la mise à niveau. Une fois la mise à niveau terminée, vous devez déplacer les fichiers d'assembly vers le nouveau dossier d'installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint.|  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]fournit une architecture extensible qui permet aux développeurs de créer des extensions personnalisées pour le traitement des données, la remise, le rendu, la sécurité et l’authentification.  
  
 Si des extensions ou des assemblys personnalisés sont utilisés dans votre installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vous pouvez utiliser le programme d'installation pour effectuer une mise à niveau, mais vous devrez peut-être déplacer des extensions vers le nouvel emplacement d'installation après la mise à niveau ou effectuer des étapes avant la mise à niveau.  
  
> [!NOTE]  
>  Le Conseiller de mise à niveau ne détecte pas si des assemblys de code personnalisés sont configurés pour une utilisation dans les rapports pour calculer des valeurs d'élément, des styles et la mise en forme. Pour plus d’informations, consultez [autres Reporting Services problèmes de mise à niveau](../../../2014/sql-server/install/other-reporting-services-upgrade-issues.md).  
  
 Si vous avez acheté des extensions personnalisées auprès d'un fournisseur de logiciels, contactez-le pour obtenir des informations supplémentaires sur la mise à niveau de vos fonctionnalités personnalisées.  
  
## <a name="corrective-action"></a>Action corrective  
 Utilisez les sections suivantes pour déterminer les étapes à effectuer en plus de la mise à niveau de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ou avant celle-ci :  
  
 [Extensions pour le traitement des données ou de remise personnalisées](#dataprocdeliver)  
  
 [Extensions de rendu personnalisées](#render)  
  
 [Extensions de sécurité ou d’authentification personnalisées sur un serveur de rapports SQL Server 2000](#secauth2000)  
  
 [Extensions de sécurité ou d'authentification personnalisées sur un serveur de rapports SQL Server 2005](#secauth2005)  
  
 Une fois la mise à niveau terminée, déplacez les assemblys d'extension vers le nouveau dossier d'installation, puis vérifiez que les extensions personnalisées fonctionnent comme prévu. Si votre extension ne fonctionne pas, vous devrez peut-être la recompiler.  
  
#### <a name="to-recompile-an-extension"></a>Pour recompiler une extension  
  
1.  Copiez le fichier Microsoft.ReportingServices.Interfaces.dll dans le dossier qui contient votre code source.  
  
2.  Ouvrez le projet qui contient vos fichiers sources et ajoutez une référence au fichier Microsoft.ReportingServices.Interfaces.dll.  
  
3.  Reconstruisez la solution pour lier l'extension.  
  
 Si vous décidez de ne pas poursuivre la mise à niveau, vous pouvez choisir de migrer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à la place. Pour plus d’instructions sur la migration d’extensions personnalisées, consultez [migration d’extensions personnalisées](#migrcustext) dans cette rubrique.  
  
###  <a name="custom-data-processing-or-delivery-extensions"></a><a name="dataprocdeliver"></a>Extensions de traitement de données ou de remise personnalisées  
 Si le Conseiller de mise à niveau détecte des extensions pour le traitement des données ou de remise personnalisées, la mise à niveau n'est pas bloquée. Toutefois, une fois la mise à niveau terminée, vous devrez peut-être effectuer des étapes supplémentaires pour que les fonctionnalités personnalisées fournies par ces extensions fonctionnent. Par exemple, vous devez effectuer des étapes supplémentaires lorsque les fichiers des extensions personnalisées sont installés dans le dossier d'installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
##### <a name="post-upgrade-steps-for-custom-data-processing-or-delivery-extensions"></a>Étapes postérieures à la mise à niveau pour les extensions pour le traitement des données ou de remise personnalisées  
  
1.  Déplacez le ou les fichiers d'extension vers le nouveau dossier du programme pour le serveur de rapports. Par défaut, le dossier du programme du serveur de rapports se trouve dans \Program Files\Microsoft SQL Server \ MSRS10_50. \<*instance_name*> serveur \Report.  
  
 Pour plus d'informations, consultez « Déploiement d'une extension pour le traitement des données » et « Implémentation d'une extension de remise » dans la documentation en ligne de SQL Server.  
  
###  <a name="custom-rendering-extensions"></a><a name="render"></a>Extensions de rendu personnalisées  
 Si le Conseiller de mise à niveau détecte des extensions de rendu personnalisées, la mise à niveau est bloquée. Vous pouvez poursuivre la mise à niveau en supprimant les entrées de configuration d'extensions personnalisées du fichier de configuration. Toutefois, les extensions personnalisées ne seront pas accessibles aux utilisateurs une fois la mise à niveau terminée. Si vous avez besoin d'extensions de rendu personnalisées après la mise à niveau, vous devez générer des extensions de rendu mises à jour ou obtenir des extensions de rendu mises à jour d'un fournisseur d'extensions personnalisées.  
  
 Vous devez effectuer des étapes pour activer une mise à niveau ou vous pouvez choisir de migrer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à la place.  
  
> [!IMPORTANT]  
>  Ne procédez pas à la mise à niveau ou à la migration de votre serveur de rapports avant d'avoir testé et vérifié que l'extension de rendu mise à jour fonctionne comme prévu.  
  
##### <a name="to-upgrade-custom-rendering-extensions"></a>Pour mettre à niveau des extensions de rendu personnalisées  
  
1.  Obtenez des extensions de rendu avec les interfaces les plus récentes.  
  
2.  Supprimez les anciennes entrées des extensions de rendu personnalisées de RSReportServer.config.  
  
3.  Mettez à niveau le serveur de rapports.  
  
4.  Une fois la mise à niveau terminée, installez les extensions mises à jour sur le serveur de rapports.  
  
 Pour plus d'informations, consultez « Implémentation d'une extension de rendu » dans la documentation en ligne de SQL Server.  
  
###  <a name="custom-security-or-authentication-extensions-on-a-sql-server-2000-report-server"></a><a name="secauth2000"></a>Extensions de sécurité ou d’authentification personnalisées sur un serveur de rapports SQL Server 2000  
 Si le Conseiller de mise à niveau détecte des extensions de sécurité ou d'authentification personnalisées sur un serveur de rapports [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], la mise à niveau est bloquée. Vous devez effectuer des étapes pour activer une mise à niveau ou vous pouvez choisir de migrer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à la place. Dans les deux cas, vous devez mettre à jour et recompiler les extensions avec les interfaces les plus récentes dans Microsoft.ReportingServices.Interfaces.dll car les interfaces ont évolué entre [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] et [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
> [!IMPORTANT]  
>  Ne procédez pas à la mise à niveau ou à la migration de votre serveur de rapports avant d'avoir testé et vérifié que l'extension de sécurité ou d'authentification mise à jour fonctionne comme prévu.  
  
 Si vous utilisez une extension d'authentification personnalisée que vous avez créée pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2000 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vous devez modifier le code source pour prendre en charge les classes et les membres nouveaux, introduits pour la création de rapports pilotés par des modèles.  
  
##### <a name="to-upgrade-custom-security-or-authentication-extensions-from-a-sql-server-2000-report-server"></a>Pour mettre à niveau des extensions de sécurité ou d’authentification personnalisées à partir d’un serveur de rapports SQL Server 2000  
  
1.  Mettez à jour et recompilez toutes les extensions de sécurité ou d'authentification avec les interfaces les plus récentes.  
  
2.  Supprimez les anciennes entrées des extensions de sécurité ou d'authentification de RSReportServer.config.  
  
3.  Mettez à niveau le serveur de rapports.  
  
4.  Une fois la mise à niveau terminée, installez les extensions mises à jour sur le serveur de rapports.  
  
 Pour plus d'informations, consultez « Implémentation d'une extension de sécurité » dans la documentation en ligne de SQL Server.  
  
###  <a name="custom-security-or-authentication-extensions-on-a-sql-server-2005-report-server"></a><a name="secauth2005"></a>Extensions de sécurité ou d’authentification personnalisées sur un serveur de rapports SQL Server 2005  
 Si le Conseiller de mise à niveau détecte des extensions de sécurité ou d'authentification personnalisées sur un serveur de rapports [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], la mise à niveau est bloquée. Vous devez effectuer des étapes pour activer une mise à niveau ou vous pouvez choisir de migrer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] à la place.  
  
##### <a name="to-upgrade-custom-security-or-authentication-extensions-from-a-sql-server-2005-report-server"></a>Pour mettre à niveau des extensions de sécurité ou d'authentification personnalisées à partir d'un serveur de rapports SQL Server 2005  
  
1.  Supprimez les anciennes entrées de configuration des extensions de sécurité ou d'authentification de RSReportServer.config.  
  
2.  Mettez à niveau le serveur de rapports.  
  
3.  Une fois la mise à niveau terminée, rajoutez les entrées de configuration dans RSReportServer.config.  
  
4.  Si les assemblys d'extension ont été installés dans l'ancien dossier d'installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], passez au nouveau dossier d'installation.  
  
 Pour plus d'informations, consultez « Implémentation d'une extension de sécurité » dans la documentation en ligne de SQL Server.  
  
###  <a name="migrating-custom-extensions"></a><a name="migrcustext"></a>Migration d’extensions personnalisées  
 Si vous décidez de migrer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] au lieu d'effectuer une mise à niveau, utilisez les étapes pour migrer des extensions personnalisées vers la nouvelle instance de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
##### <a name="to-migrate-custom-extensions-to-a-new-reporting-services-instance"></a>Pour migrer des extensions personnalisées vers une nouvelle instance de Reporting Services  
  
1.  Générez ou obtenez des extensions mises à jour avec les interfaces de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] les plus récentes.  
  
2.  Migre le serveur de rapports vers une nouvelle instance.  
  
3.  Configurez les extensions sur la nouvelle instance.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau de Reporting Services &#40;conseiller de mise à niveau&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
