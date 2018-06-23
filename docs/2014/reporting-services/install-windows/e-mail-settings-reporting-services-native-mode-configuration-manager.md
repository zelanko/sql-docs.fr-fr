---
title: Paramètres de messagerie - Gestionnaire de Configuration (SSRS en Mode natif) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rsconfigtool.emailsettings.f1
helpviewer_keywords:
- SQL11.rsconfigtool.emailsettings.F1
ms.assetid: cdad1529-bfa6-41fb-9863-d9ff1b802577
caps.latest.revision: 7
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 96e3318045d058a7d953684fa05bfd72aed9bd69
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152503"
---
# <a name="e-mail-settings---configuration-manager-ssrs-native-mode"></a>Paramètres de messagerie - Gestionnaire de configuration (SSRS en mode natif)
  Utilisez cette page pour spécifier les paramètres du protocole SMTP (Simple Mail Transfer Protocol) qui activent la remise du courrier électronique à partir du serveur de rapports. Vous pouvez utiliser l'extension de remise du courrier électronique Report Server pour distribuer des rapports ou des notifications de traitement de rapport par le biais d'abonnements à la messagerie. L'extension de remise par messagerie Report Server nécessite un serveur SMTP et une adresse de messagerie à utiliser dans le champ De :.  
  
 Des paramètres de configuration supplémentaires peuvent être utilisés pour personnaliser davantage les abonnements à la messagerie, notamment les paramètres qui limitent les hôtes de serveur de messagerie et la disponibilité de l'extension de rendu. Vous ne pouvez pas spécifier ces paramètres dans le [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager. Pour configurer les paramètres supplémentaires, vous devez modifier manuellement le fichier RSReportServer.config. Pour plus d’informations, consultez [configurer un serveur de rapports pour la remise du courrier électronique &#40;Gestionnaire de Configuration de SSRS&#41; ](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) et [fichiers de Configuration de Reporting Services](../report-server/reporting-services-configuration-files.md) dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation En ligne.  
  
 Pour ouvrir cette page, démarrez le Gestionnaire de Configuration de Reporting Services, puis cliquez sur **paramètres de messagerie** dans le volet de navigation. Pour plus d’informations, consultez [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif.  
  
## <a name="options"></a>Options  
 **Adresse d’expéditeur**  
 Spécifie l'adresse de messagerie à utiliser dans le champ De : d'un message généré. Vous devez spécifier un compte d'utilisateur qui a l'autorisation d'envoyer du courrier depuis le serveur SMTP.  
  
 **Méthode actuelle de remise SMTP**  
 Spécifie que le message du serveur de rapports est acheminé par le biais d'un serveur SMTP. Il s'agit du seul mode de remise que vous pouvez spécifier dans le Gestionnaire de configuration de Reporting Services.  
  
 Un autre mode de remise consiste à utiliser un répertoire de collecte local du service SMTP. Vous pouvez utiliser ce mode de remise si aucun service réseau SMTP n'est disponible. Pour spécifier un répertoire de collecte local du service SMTP, vous devez modifier le fichier RSReportServer.config. Si vous éditez le fichier de configuration pour qu'il utilise un répertoire de collecte local du service SMTP, le Gestionnaire de configuration de Reporting Services définit l'option **Mode de remise** sur *Personnalisé* pour indiquer que le mode de remise est spécifié dans le fichier de configuration.  
  
 Dans le fichier de configuration, la méthode de remise est définie via la `SendUsing` paramètre de configuration. Pour plus d’informations sur la spécification de la `SendUsing` , consultez [configurer un serveur de rapports pour la remise du courrier électronique &#40;Gestionnaire de Configuration de SSRS&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).  
  
 **Serveur SMTP**  
 Spécifiez le serveur ou la passerelle SMTP à utiliser. Vous pouvez utiliser un serveur local ou un serveur SMTP sur votre réseau.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer un serveur de rapports pour la remise du courrier électronique &#40;Gestionnaire de Configuration de SSRS&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)   
 [Rubriques d’aide F1 Gestionnaire de Configuration de Reporting Services &#40;SSRS en Mode natif&#41;](../../sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)  
  
  