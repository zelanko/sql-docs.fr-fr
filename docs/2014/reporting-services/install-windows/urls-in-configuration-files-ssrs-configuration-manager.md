---
title: URL des fichiers de configuration (Gestionnaire de configuration de SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- URL configuration [Reporting Services]
ms.assetid: 4f5e7fe0-b5b1-4665-93d4-80dce12d6b14
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 48deeb3ba6badb1d01b895467f2a8418bdf37ba9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "80380710"
---
# <a name="urls-in-configuration-files--ssrs-configuration-manager"></a>URL des fichiers de configuration (Gestionnaire de configuration de SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] stocke les paramètres d’application dans un fichier RSReportServer.config. Ce fichier contient des paramètres de configuration pour les URL et pour les réservations d'URL. Ces paramètres de configuration ont des règles de modification et des objectifs très différents. Si vous êtes habitué à la modification de fichiers de configuration pour régler un déploiement, cette rubrique peut vous aider à comprendre comment chaque paramètre URL est utilisé.  
  
## <a name="url-settings-in-rsreportserverconfig-file"></a>Paramètres d'URL du fichier RSReportServer.config  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] stocke les URL pour l’accès aux applications et aux rapports, et pour connecter les composants web frontaux à un serveur de rapports principal.  
  
#### <a name="urls-for-application-access"></a>URL d'accès aux applications  
 Les URL permettent d'accéder au service Web Report Server et au Gestionnaire de rapports. Pour configurer les URL, vous devez utiliser l'outil de configuration de Reporting Services. L'outil crée les réservations d'URL pour chaque application dans HTTP.SYS et ajoute des entrées pour les URL dans la section `URLReservations` de RSReportServer.config.  
  
-   Pour afficher les descriptions de chaque élément dans `URLReservations` la section, consultez [fichier de configuration RSReportServer](../report-server/rsreportserver-config-configuration-file.md) dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Pour plus d’informations sur la syntaxe de l' `UrlString` élément, consultez [syntaxe de réservation d’URL &#40;SSRS Configuration Manager&#41;](url-reservation-syntax-ssrs-configuration-manager.md).  
  
-   Pour obtenir des instructions sur la configuration des URL pour l’accès aux applications, consultez [Configurer une URL &#40;Gestionnaire de configuration de SSRS&#41;](configure-a-url-ssrs-configuration-manager.md).  
  
#### <a name="urls-for-report-access"></a>URL d'accès aux rapports  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] inclut une extension de remise par messagerie de serveur de rapports que vous pouvez utiliser pour envoyer les liens de rapport ou les pièces jointes. Un lien de rapport est construit lorsque le rapport est remis. L'extension de remise par messagerie de serveur de rapports utilise le paramètre `UrlRoot` du fichier de configuration pour créer le lien. `UrlRoot` est également utilisé pour résoudre les liens d'un rapport rendu et généré via un traitement des rapports sans assistance.  
  
 `UrlRoot` est spécifié automatiquement dans le fichier RSReportServer.config lorsque vous configurez les URL pour l'accès aux applications. Si vous modifiez cette valeur dans le fichier de configuration, vous devez spécifier l'adresse URL valide d'un service Web Report Server connecté à une base de données de serveur de rapports qui contient les rapports que vous souhaitez remettre. Vous pouvez spécifier un seul élément `UrlRoot` pour une instance de serveur de rapports unique ; une seule entrée `UrlRoot` peut exister dans le fichier RSReportServer.config pour toute instance de serveur de rapports donnée. Si vous avez plusieurs URL réservées pour le service Web Report Server, vous devez choisir l'une des valeurs disponibles pour `UrlRoot`.  
  
 Dans la plupart des cas, vous n'avez pas besoin de modifier `UrlRoot`. Toutefois, si le serveur de rapports est accessible par le biais d’une URL complète et que vous n’avez pas configuré une URL qui utilise un en-tête d’hôte pour le nom de site complet, vous devez modifier le fichier `UrlRoot` RSReportServer. config manuellement pour définir sur l’URL complète du serveur de rapports qui sera utilisée pour le `https://www.adventure-works.com/mywebapp/reportserver`rendu du rapport (par exemple,).  
  
#### <a name="urls-connecting-report-manager-and-web-parts-to-the-report-server-web-service"></a>URL connectant le Gestionnaire de rapports et les composants WebPart au service Web Report Server  
 Le Gestionnaire de rapports et les composants WebPart SharePoint 2.0 pour Reporting Services sont les composants Web frontaux qui se connectent à un serveur de rapports. Les URL utilisées pour se connecter à un serveur de rapports principal sont les suivantes :  
  
-   `ReportServerUrl` (élément utilisé par le Gestionnaire de rapports)  
  
-   `ReportServerExternalUrl` (élément utilisé par les composants WebPart)  
  
> [!NOTE]  
>  Les versions antérieures de Reporting Services incluaient l'élément `ReportServerVirtualDirectory`. Cette valeur est obsolète dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et les versions ultérieures. Si vous avez mis à niveau une installation existante et utilisez un fichier de configuration qui contient ce paramètre, le serveur de rapports ne lit plus cette valeur.  
  
 Le tableau suivant récapitule toutes les URL pouvant être spécifiées dans un fichier de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
|Paramètre|Usage|Description|  
|-------------|-----------|-----------------|  
|`ReportServerUrl`|facultatif. Cet élément n'est pas inclus dans le fichier RSReportServer.config à moins que vous ne l'ajoutiez vous-même. Définissez cet élément uniquement si vous configurez l'un des scénarios suivants :<br /><br /> Le Gestionnaire de rapports fournit un accès Web frontal à un service Web Report Server qui s'exécute sur un autre ordinateur ou sur une instance différente du même ordinateur.<br /><br /> Lorsque vous avez plusieurs URL vers un serveur de rapports et que vous souhaitez que le Gestionnaire de rapports utilise une URL spécifique.<br /><br /> Vous avez une URL du serveur de rapports spécifique que vous souhaitez voir utilisée par toutes les connexions du Gestionnaire de rapports.<br /><br /> Par exemple, vous pouvez activer l'accès du Gestionnaire de rapports pour tous les ordinateurs du réseau, tout en requérant que le Gestionnaire de rapports se connecte au serveur de rapports à travers une connexion locale. Dans ce cas, vous pouvez configurer `ReportServerUrl` sur «http://localhost/reportserver».<br /><br /> <br /><br /> Pour obtenir des instructions sur la façon d’implémenter ces scénarios, consultez [configurer gestionnaire de rapports mode natif &#40;&#41;](../report-server/configure-web-portal.md) dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|Cette valeur spécifie l'URL du service Web Report Server. Cette valeur est lue par l'application du Gestionnaire de rapports au démarrage. Si cette valeur est définie, le Gestionnaire de rapports se connecte au serveur de rapports spécifié dans l'URL.<br /><br /> Par défaut, le Gestionnaire de rapports fournit un accès Web frontal à un service Web Report Server qui s'exécute au sein de la même instance du serveur de rapports que le Gestionnaire de rapports. Toutefois, si vous souhaitez utiliser le Gestionnaire de rapports avec un service Web Report Server qui fait partie d'une autre instance ou s'exécute dans une instance d'un autre ordinateur, vous pouvez définir cette URL de façon à diriger le Gestionnaire de rapports pour qu'il se connecte au service Web Report Server externe.<br /><br /> Si un certificat SSL (Secure Sockets Layer) est installé sur le serveur de rapports auquel vous êtes connecté, la valeur de l'élément `ReportServerUrl` doit être le nom du serveur inscrit pour ce certificat. Si l'erreur « La connexion sous-jacente a été fermée. Impossible d'établir une relation de confiance pour le canal sécurisé SSL/TLS » s'affiche, définissez l'élément `ReportServerUrl` avec le nom de domaine complet du serveur pour lequel le certificat SSL a été émis. Par exemple, si le certificat est inscrit pour **https:\//adventure-works.com.onlinesales**, l’URL du serveur de rapports sera **https:\//adventure-works.com.onlinesales/reportserver**.|  
|`ReportServerExternalUrl`|facultatif. Cet élément n'est pas inclus dans le fichier RSReportServer.config à moins que vous ne l'ajoutiez vous-même.<br /><br /> Définissez cet élément uniquement si vous utilisez les composants WebPart de SharePoint 2.0 et que vous souhaitez que les utilisateurs soient en mesure d'extraire un rapport et de l'ouvrir dans une nouvelle fenêtre de navigateur.<br /><br /> Ajoutez <`ReportServerExternalUrl`> sous l’élément `ReportServerUrl` <>, puis affectez-lui un nom de serveur de rapports complet qui se résout en une instance de serveur de rapports lorsque vous y accédez dans une fenêtre de navigateur distincte. Ne supprimez pas `ReportServerUrl` <>.<br /><br /> L'exemple suivant illustre la syntaxe :<br /><br /> `<ReportServerExternalUrl>http://myserver/reportserver</ReportServerExternalUrl>`|Cette valeur est utilisée par les composants WebPart de SharePoint 2.0.<br /><br /> Dans les versions précédentes, il était recommandé que vous définissiez cette valeur pour déployer le Générateur de rapport sur un serveur de rapports Internet. Il s'agit d'un scénario de déploiement non testé. Si vous utilisiez ce paramètre par le passé pour gérer l'accès Internet au Générateur de rapports, vous devez prévoir une autre stratégie.|  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer des URL de serveurs de rapports &#40;Gestionnaire de configuration de SSRS&#41;](configure-report-server-urls-ssrs-configuration-manager.md)   
 [Configurer une URL &#40;Gestionnaire de configuration de SSRS&#41;](configure-a-url-ssrs-configuration-manager.md)  
  
  
