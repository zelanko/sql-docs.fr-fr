---
title: URL du service Web (SSRS en mode natif) | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.reportservervirtualdirectory.F1
helpviewer_keywords:
- Reporting Services, Web service
ms.assetid: 9d210b5d-2a08-4e56-a4f5-c16715b00d79
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 01e5393ae638ddcecd04211a0a7e01e8116346a9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "71952365"
---
# <a name="web-service-url-ssrs-native-mode"></a>URL de service Web (SSRS en mode natif)
  Utilisez la page URL du service Web pour configurer ou modifier l'URL permettant d'accéder au serveur de rapports. Une *réservation d'URL* est créée en fonction de l'URL que vous spécifiez. La réservation d'URL définit la syntaxe et les règles de toutes les URL qui peuvent être utilisées par la suite pour accéder au service Web Report Server. Elle spécifie le préfixe, l'hôte, le port et le répertoire virtuel pour le service Web Report Server. Selon la façon dont vous spécifiez l'hôte, plusieurs URL peuvent être possibles pour une réservation unique. La valeur par défaut pour l'hôte spécifie un caractère générique fort. Un caractère générique fort vous permet de spécifier dans une URL un nom d'hôte qui peut être résolu sur l'ordinateur qui héberge le serveur de rapports. Pour plus d’informations sur la configuration et les réservations d’URL, consultez [configurer une url &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md) et [configurer des URL de serveur de rapports &#40;SSRS Configuration Manager&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Mode natif.  
  
 Pour ouvrir cette page, démarrez le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et cliquez sur **URL du service Web** dans le volet de navigation. Pour plus d’informations, consultez [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 Cette page fournit les valeurs utilisées communément dans les URL de serveurs de rapports. Si vous souhaitez créer des URL supplémentaires, utiliser les en-têtes de l'hôte ou spécifier l'adresse IP dans un format particulier, cliquez sur **Avancé**.  
  
 Un lien vers le service Web apparaît sur cette page après que vous avez cliqué sur **Appliquer**. Si vous cliquez sur ce lien avant que la base de données du serveur de rapports ne soit créée, vous pouvez vous attendre à voir l'erreur « Page introuvable ». Cette erreur n'apparaît plus une fois la base de données configurée. Pour plus d’informations, consultez [Créer une base de données du serveur de rapports en mode natif &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md).  
  
 Si vous avez réinstallé [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et constatez que vous obtenez une erreur lors de la tentative d'utilisation de la valeur d'adresse IP par défaut « Assigné » et le port 80, vous pouvez généralement résoudre l'erreur en recréant l'URL après avoir redémarré le service.  
  
## <a name="options"></a>Options  
 **Répertoire virtuel**  
 Spécifie le nom de répertoire virtuel pour le service Web Report Server. Vous ne pouvez avoir qu'un nom virtuel pour chaque instance du service Web Report Server sur le même ordinateur.  
  
 **Adresse IP**  
 Identifie le serveur de rapports sur un réseau TCP/IP. Les valeurs valides sont les suivantes :  
  
-   **Assigné** spécifie que chacune des adresses IP assignées à l'ordinateur peut être utilisée dans une URL qui pointe sur une application du serveur de rapports. Cette valeur comprend également les noms d'hôte conviviaux (tels que les noms d'ordinateur) qui peuvent être résolus par un serveur de noms de domaine en une adresse IP assignée à l'ordinateur. Il s'agit de la valeur par défaut pour une URL [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
-   **Non assigné** spécifie que le serveur de rapports accepte toute demande qui n'a pas de correspondance exacte pour l'adresse IP ou le nom d'hôte. N'utilisez pas cette valeur si une autre application Web l'utilise déjà. Sinon, vous interromprez le service pour l'autre application.  
  
-   **127.0.0.1** est utilisée pour l'accès à localhost. Cette valeur prend en charge l'administration locale sur le serveur de rapports. Si vous sélectionnez uniquement cette valeur, seuls les utilisateurs qui se connectent localement au serveur de rapports ont accès à l'application.  
  
-   *Nnn.nnn.nnn.nnn* est l'adresse IPv4 d'une carte réseau sur votre ordinateur. Si votre réseau utilise l’adressage IPv6, l’adresse IP sera une valeur 128 bits de champs de 8 4 octets semblable au format suivant : \<> d’en-tête :*nnnn : nnnn : nnnn : nnnn*  
  
     Si vous avez plusieurs cartes, une adresse IP apparaît pour chacune d'elles. Si vous sélectionnez uniquement cette valeur, elle limite l'accès de l'application à la seule adresse IP (et à tout nom d'hôte mappé sur cette adresse par un serveur de noms de domaine). Vous ne pouvez pas utiliser localhost pour accéder à un serveur de rapports, et vous ne pouvez pas utiliser les adresses IP des autres cartes réseau installées sur le serveur de rapports.  
  
 **Port TCP**  
 Spécifie le port que le serveur de rapports surveille pour les requêtes HTTP pour les URL qui incluent le nom de répertoire virtuel de serveur de rapports.  
  
 **Certificat SSL**  
 Lie un certificat à l'adresse IP que vous avez spécifiée. Le certificat doit être installé et configuré sur le serveur. Reporting Services ne fournit pas de fonctionnalités pour gérer des certificats. Le certificat doit être émis sur un nom d'hôte ou un nom d'ordinateur qui se résout en une adresse IP. Par exemple, pour utiliser un certificat délivré à http://salesreports, l’adresse IP que vous avez spécifiée doit être résolue en un serveur nommé « salesreports ».  
  
 Si vous utilisez un certificat, vous devez également modifier le paramètre de configuration `UrlRoot` dans le fichier RSReportServer.config, afin qu'il spécifie le nom complet de l'ordinateur pour lequel le certificat est enregistré. Pour plus d’informations, consultez [Configurer des connexions SSL sur un serveur de rapports en mode natif](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md) dans la documentation en ligne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Port SSL**  
 Spécifie le port pour les connexions SSL.  
  
 **URLs**  
 Affiche les URL définies pour l'instance en cours du serveur de rapports.  
  
 **Avancé**  
 Cliquez pour créer des URL supplémentaires pour l'instance d'application en cours.  
  
> [!NOTE]
>  Si vous disposez de liaisons SSL et de réservations d'URL existantes et souhaitez modifier la liaison SSL, vous pouvez utiliser un certificat ou un en-tête d'hôte différent. Il est recommandé de réaliser les étapes suivantes dans l'ordre indiqué :  
> 
>  1.  Commencez par supprimer toutes les réservations d'URL.  
> 2.  Puis, supprimez toutes les liaisons SSL.  
> 3.  puis de recréer les URL et les liaisons SSL.  
> 
>  Les étapes précédentes peuvent être effectuées à partir du Gestionnaire de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
> 
>  Microsoft Windows prend en charge une liaison pour chaque combinaison d'adresse IP/port. Si vous configurez un serveur de rapports de façon à utiliser une valeur d'en-tête d'hôte spécifique et le certificat sur la combinaison port/adresse IP est également émis à une valeur d'en-tête d'hôte différente, un avertissement indiquant que le certificat ne correspond pas à l'URL utilisée s'affiche dans le navigateur.  
> 
>  Pour corriger le problème, supprimez toutes les liaisons, puis créez des liaisons possédant des paramètres uniques, ou configurez l'inscription d'URL Reporting Services à l'aide de caractères génériques.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de configuration de Reporting Services les rubriques d’aide F1 &#40;le mode natif SSRS&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-f1-help-topics-ssrs-native-mode.md)   
 [Configurer des URL de serveurs de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
  
  
