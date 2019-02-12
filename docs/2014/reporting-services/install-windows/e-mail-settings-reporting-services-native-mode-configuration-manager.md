---
title: Paramètres de messagerie - Gestionnaire de Configuration (Mode natif SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- sql12.rsconfigtool.emailsettings.f1
helpviewer_keywords:
- SQL11.rsconfigtool.emailsettings.F1
ms.assetid: cdad1529-bfa6-41fb-9863-d9ff1b802577
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 1340e42824aabd3e4d32cc844f3061be90f97e52
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56031986"
---
# <a name="e-mail-settings---configuration-manager-ssrs-native-mode"></a>Paramètres de messagerie - Gestionnaire de configuration (SSRS en mode natif)
  Utilisez cette page pour spécifier les paramètres du protocole SMTP (Simple Mail Transfer Protocol) qui activent la remise du courrier électronique à partir du serveur de rapports. Vous pouvez utiliser l'extension de remise du courrier électronique Report Server pour distribuer des rapports ou des notifications de traitement de rapport par le biais d'abonnements à la messagerie. L'extension de remise par messagerie Report Server nécessite un serveur SMTP et une adresse de messagerie à utiliser dans le champ De :.  
  
 Des paramètres de configuration supplémentaires peuvent être utilisés pour personnaliser davantage les abonnements à la messagerie, notamment les paramètres qui limitent les hôtes de serveur de messagerie et la disponibilité de l'extension de rendu. Vous ne pouvez pas spécifier ces paramètres dans le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Pour configurer les paramètres supplémentaires, vous devez modifier manuellement le fichier RSReportServer.config. Pour plus d’informations, consultez [configurer un serveur de rapports pour la remise du courrier électronique &#40;Gestionnaire de Configuration de SSRS&#41; ](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md) et [fichiers de Configuration de Reporting Services](../report-server/reporting-services-configuration-files.md) dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation En ligne.  
  
 Pour ouvrir cette page, démarrez le Gestionnaire de Configuration de Reporting Services et cliquez sur **paramètres de messagerie** dans le volet de navigation. Pour plus d’informations, consultez [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif.  
  
## <a name="options"></a>Options  
 **Adresse d’expéditeur**  
 Spécifie l'adresse de messagerie à utiliser dans le champ De : d'un message généré. Vous devez spécifier un compte d'utilisateur qui a l'autorisation d'envoyer du courrier depuis le serveur SMTP.  
  
 **Méthode actuelle de remise SMTP**  
 Spécifie que le message du serveur de rapports est acheminé par le biais d'un serveur SMTP. Il s'agit du seul mode de remise que vous pouvez spécifier dans le Gestionnaire de configuration de Reporting Services.  
  
 Un autre mode de remise consiste à utiliser un répertoire de collecte local du service SMTP. Vous pouvez utiliser ce mode de remise si aucun service réseau SMTP n'est disponible. Pour spécifier un répertoire de collecte local du service SMTP, vous devez modifier le fichier RSReportServer.config. Si vous éditez le fichier de configuration pour qu'il utilise un répertoire de collecte local du service SMTP, le Gestionnaire de configuration de Reporting Services définit l'option **Mode de remise** sur *Personnalisé* pour indiquer que le mode de remise est spécifié dans le fichier de configuration.  
  
 Dans le fichier de configuration, le mode de remise est défini par le biais du paramètre de configuration `SendUsing`. Pour plus d’informations sur la spécification de la `SendUsing` définition, consultez [configurer un serveur de rapports pour la remise du courrier électronique &#40;Gestionnaire de Configuration de SSRS&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md).  
  
 **Serveur SMTP**  
 Spécifiez le serveur ou la passerelle SMTP à utiliser. Vous pouvez utiliser un serveur local ou un serveur SMTP sur votre réseau.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer un serveur de rapports pour la remise du courrier électronique &#40;Gestionnaire de Configuration de SSRS&#41;](../../sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)   
 [Rubriques d’aide F1 Gestionnaire de Configuration de Reporting Services &#40;SSRS en Mode natif&#41;](../../sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)  
  
  
