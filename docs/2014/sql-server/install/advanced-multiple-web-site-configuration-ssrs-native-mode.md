---
title: Configuration avancée de plusieurs Web Site (Mode natif SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- SQL12.rsconfigtool.advancedmultiplewebsiteconfig.F1
ms.assetid: af4ede43-2225-45b5-ae7e-9202411551ba
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: d6860e41991d00e6cd0c2869413dca110422c4e6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63226013"
---
# <a name="advanced-multiple-web-site-configuration-ssrs-native-mode"></a>Configuration avancée de plusieurs sites Web (SSRS en mode natif)
  Utilisez cette boîte de dialogue pour créer et gérer les URL permettant d'accéder à un serveur de rapports ou au Gestionnaire de rapports. La boîte de dialogue **Configuration de site Web multiple avancée** est utilisée pour créer des URL supplémentaires, des URL personnalisées qui incluent un nom d'en-tête de l'hôte ou spécifier une adresse IP au format IPv4 ou IPv6.  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif.  
  
 La création de plusieurs URLS est utile si vous souhaitez configurer les différents moyens d'accéder à un serveur de rapports. Par exemple, l'accès au serveur de rapports via une connexion intranet et extranet requiert en général que vous ayez une URL différente pour chaque type de connexion.  
  
 Pour ouvrir la boîte de dialogue **Configuration de site Web multiple avancée** , cliquez sur **Avancé** dans l' **URL du service Web** ou sur la page **URL du Gestionnaire de rapports** dans le Gestionnaire de configuration de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Une fois la boîte de dialogue **Configuration de site Web multiple avancée** ouverte, vous pouvez cliquer sur **Ajoutez** ou sur **Modifier** pour définir de nouvelles URL ou modifier ou supprimer les URL existantes.  
  
 Cliquez sur **OK** pour enregistrer vos modifications. Si vous ajoutez ou supprimez des URL, mais en revanche fermez la boîte de dialogue sans cliquer d'abord sur **OK**, vos modifications seront perdues.  
  
## <a name="options"></a>Options  
 **Adresse IP**  
 Identifie le serveur de rapports sur un réseau TCP/IP. Les valeurs valides sont les suivantes :  
  
-   **Assigné** spécifie que chacune des adresses IP assignées à l'ordinateur peut être utilisée dans une URL qui pointe sur une application du serveur de rapports. Cette valeur comprend également les noms d'hôte conviviaux (tels que les noms d'ordinateur) qui peuvent être résolus par un serveur de noms de domaine en une adresse IP assignée à l'ordinateur. Il s'agit de la valeur par défaut pour une URL [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
-   **Non assigné** spécifie que le serveur de rapports accepte toute demande qui n'a pas de correspondance exacte pour l'adresse IP ou le nom d'hôte. N'utilisez pas cette valeur si une autre application Web l'utilise déjà. Sinon, vous interromprez le service pour l'autre application.  
  
-   **127.0.0.1** est utilisée pour l'accès à localhost. Cette valeur prend en charge l'administration locale sur le serveur de rapports. Si vous sélectionnez uniquement cette valeur, seuls les utilisateurs qui se connectent localement au serveur de rapports ont accès à l'application.  
  
-   *Nnn.nnn.nnn.nnn* est l'adresse IPv4 d'une carte réseau sur votre ordinateur. Si votre réseau utilise l’adressage IPv6, l’adresse IP sera une valeur 128 bits de 8 champs de 4 octets semblable au format suivant : \<en-tête > :*nnnn:nnnn:nnnn:nnnn*.  
  
     Si vous avez plusieurs cartes, une adresse IP apparaît pour chacune d'elles. Si vous sélectionnez uniquement cette valeur, elle limite l'accès de l'application à la seule adresse IP (et à tout nom d'hôte mappé sur cette adresse par un serveur de noms de domaine). Vous ne pouvez pas utiliser localhost pour accéder à un serveur de rapports, et vous ne pouvez pas utiliser les adresses IP des autres cartes réseau installées sur le serveur de rapports.  
  
 **Port**  
 Spécifie le port que surveille le serveur de rapports pour les demandes. Le port par défaut est le port 80. Si vous utilisez le port 80, vous n'avez pas à l'inclure dans l'URL. Si vous utilisez un autre numéro de port, vous devez toujours l’inclure dans l’URL (par exemple, http://localhost:8181/reports).  
  
 **En-tête de l'hôte**  
 Si vous avez déjà un en-tête de l'hôte défini sur un serveur de noms de domaine qui se résout sur votre ordinateur, vous pouvez spécifier cet en-tête de l'hôte dans une URL que vous configurez pour l'accès au serveur de rapports.  
  
 Un en-tête de l'hôte est un nom unique qui permet à plusieurs sites Web de partager une même adresse IP et un même port. Les noms d'en-tête de l'hôte sont plus faciles à mémoriser et à taper que les adresses IP et les numéros de port. Un exemple de nom d'en-tête de l'hôte peut être www.adventure-works.com.  
  
 **Port SSL**  
 Spécifie le port pour les connexions SSL. Le numéro de port SSL par défaut est 443.  
  
 **Certificat SSL**  
 Spécifie le nom de certificat d'un certificat SSL que vous avez installé sur cet ordinateur. Si le certificat est mappé sur un caractère générique, vous pouvez l'utiliser pour une connexion de serveur de rapports.  
  
 Spécifie le nom complet de l'ordinateur pour lequel le certificat est enregistré. Le nom que vous spécifiez doit être identique au nom pour lequel le certificat est enregistré.  
  
 Un certificat doit être installé pour utiliser cette option. Vous devez également modifier le paramètre de configuration UrlRoot dans le fichier RSReportServer.config, afin qu'il spécifie le nom complet de l'ordinateur pour lequel le certificat est enregistré. Pour plus d’informations, consultez [Configurer des connexions SSL sur un serveur de rapports en mode natif](../../reporting-services/security/configure-ssl-connections-on-a-native-mode-report-server.md) dans la documentation en ligne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Délivré à**  
 Nom de l'ordinateur sur lequel le certificat a été créé.  
  
 **Ajouter**  
 Définissez une URL supplémentaire.  
  
 **Modifier**  
 Modifiez une partie de la syntaxe d'URL.  
  
 **Supprimer**  
 Supprimez une entrée URL de la liste.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de configuration de Reporting Services &#40;mode natif&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Configurer une URL &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)   
 [Configurer des URL de serveurs de rapports &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
  
  
