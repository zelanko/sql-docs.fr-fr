---
title: Propriétés TCP/IP (onglet des adresses IP) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- ports [SQL Server], listening on
- listening [SQL Server], on ports
ms.assetid: 4c17ed45-9da7-4bec-bce6-970109fe7365
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: afb62458cb76a1187dce06efadeca00fc8a382f2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63151446"
---
# <a name="tcp-ip-properties-ip-addresses-tab"></a>Propriétés TCP/IP (onglet des adresses IP)
  La boîte de dialogue **Propriétés TCP/IP (onglet Adresses IP)** permet de configurer les options du protocole TCP/IP pour une adresse IP spécifique. Seules les options **Ports TCP dynamiques** et **Port TCP** peuvent être configurées pour toutes les adresses en une seule fois en sélectionnant **IPAll**.  
  
 Les modifications sont appliquées au redémarrage de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations sur le démarrage et l’arrêt du service SQL Server Browser, consultez Comment : Démarrer et arrêter le Service SQL Server Browser dans la documentation en ligne.  
  
## <a name="static-vs-dynamic-ports"></a>Ports statiques et Ports dynamiques  
 L'instance par défaut de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] écoute les connexions entrantes sur le port 1433. Le port peut être modifié pour des raisons de sécurité ou parce qu'une application cliente le requiert. Par défaut, les instances nommées (y compris SQL Server Express) sont configurées pour être à l'écoute sur les ports dynamiques. Pour configurer un port statique, ne complétez pas la zone **Ports TCP dynamiques** et spécifiez un numéro de port disponible dans la zone **Port TCP** . Pour plus d'informations sur l'ouverture de ports dans le pare-feu, consultez Configuration du Pare-feu Windows pour autoriser l'accès à SQL Server dans la documentation en ligne.  
  
## <a name="dynamic-ports"></a>Ports dynamiques  
 Au démarrage, lorsqu'une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configurée pour écouter sur des ports dynamiques, elle vérifie s'il existe un port disponible dans le système d'exploitation et ouvre un point de terminaison pour ce port. Les connexions entrantes doivent spécifier ce numéro de port pour se connecter. Étant donné qu'il est possible de modifier le numéro de port à chaque démarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser pour analyser les ports et diriger les connexions entrantes vers le port actif de cette instance. L'utilisation des ports dynamiques complique la connexion de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par le biais d'un pare-feu, car le numéro de port peut changer lors du redémarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ce qui nécessite la modification des paramètres du pare-feu. Pour éviter les problèmes de connexion liés à un pare-feu, configurez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de manière à utiliser un port statique.  
  
## <a name="options"></a>Options  
 **Actif**  
 Indique que l'adresse IP est active sur l'ordinateur. Option non disponible pour **IPAll**.  
  
 **Activé**  
 Si la propriété **Écouter tout** des **Propriétés TCP/IP (onglet Protocole)** a la valeur **Non**, elle indique si SQL Server est à l’écoute sur l’adresse IP. Si la propriété **Écouter tout** des **Propriétés TCP/IP (onglet Protocole)** a la valeur **Oui**, la propriété est ignorée. Option non disponible pour **IPAll**.  
  
 **Adresse IP**  
 Afficher ou modifier l'adresse IP utilisée par cette connexion. Indique l'adresse IP utilisée par l'ordinateur et l'adresse de boucle IP, 127.0.0.1. Option non disponible pour **IPAll**. L'adresse IP peut être au format IPv4 ou IPv6.  
  
 **Ports TCP dynamiques**  
 Aucune valeur si les ports ne sont pas activés. Pour utiliser les ports dynamiques, indiquez la valeur 0.  
  
 Pour **IPAll**, affiche le numéro du port dynamique utilisé.  
  
 **Port TCP**  
 Afficher ou modifier le port sur lequel écoute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . L'instance par défaut de [!INCLUDE[ssDE](../../includes/ssde-md.md)] écoute sur le port 1433 par défaut.  
  
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] peut écouter sur plusieurs ports sur la même adresse IP, répertorie les ports, séparés par des virgules, au format 1433,1500,1501. Ce champ est limité à 2 047 caractères.  
  
 Pour configurer une seule adresse IP pour l’écoute sur plusieurs ports, le paramètre **Écouter tout** doit également avoir la valeur **Non**, sous l’onglet **Protocoles** de la boîte de dialogue **Propriétés de TCP/IP** . Pour plus d’informations, consultez « Comment : Configurer le moteur de base de données à écouter sur plusieurs Ports TCP » dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la documentation en ligne.  
  
## <a name="adding-or-removing-ip-addresses"></a>Ajout ou suppression d'adresses IP  
 Le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affiche les adresses IP qui étaient disponibles au moment de l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les adresses IP disponibles peuvent changer lorsque : des cartes réseau sont ajoutées ou supprimées, une adresse IP affectée dynamiquement arrive à expiration, une structure de réseau est reconfigurée ou un ordinateur est déplacé physiquement, par exemple si un ordinateur portable est connecté au réseau d'un autre bâtiment. Pour changer une adresse IP, modifiez la zone **Adresse IP** , puis redémarrez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Choix d'un protocole réseau](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)   
 [Création d’une chaîne de connexion valide à l’aide du protocole TCP/IP](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)   
 [Service SQL Server Browser](../../../2014/tools/configuration-manager/sql-server-browser-service.md)  
  
  
