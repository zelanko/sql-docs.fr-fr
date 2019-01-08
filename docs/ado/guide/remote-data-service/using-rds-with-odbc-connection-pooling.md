---
title: À l’aide des services Bureau à distance avec une connexion ODBC mise en pool | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connection pooling in RDS [ADO]
ms.assetid: e8b912c1-da5b-4e85-a000-1e6648a94237
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7fbc75772a48b4990ebbc31877a3f7a95b442087
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52506352"
---
# <a name="using-rds-with-odbc-connection-pooling"></a>Utilisation de RDS avec le regroupement de connexions ODBC
Si vous utilisez une source de données ODBC, vous pouvez utiliser la connexion pooling (option) dans Internet Information Services (IIS) pour bénéficier d’une gestion de la charge client hautes performances. Le regroupement de connexions est un gestionnaire de ressources pour les connexions, maintient l’état ouvert sur les connexions fréquemment utilisées.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Pour activer le regroupement de connexions, reportez-vous à la documentation d’Internet Information Services.  
  
 Veuillez noter que l’activation le regroupement de connexions peut imposer le serveur Web d’autres restrictions, comme indiqué dans la documentation de Microsoft Internet Information Services.  
  
 Pour vous assurer que le regroupement de connexions est stable et offre des gains de performances supplémentaires, vous devez configurer Microsoft SQL Server pour utiliser la bibliothèque réseau de TCP/IP Socket.  
  
 Pour ce faire, vous devez :  
  
-   Configurez l’ordinateur SQL Server pour utiliser des Sockets TCP/IP.  
  
-   Configurer le serveur Web pour utiliser des Sockets TCP/IP.  
  
## <a name="configuring-the-sql-server-computer-to-use-tcpip-sockets"></a>Configuration de l’ordinateur SQL Server pour utiliser des Sockets TCP/IP  
 Sur l’ordinateur SQL Server, exécutez le programme d’installation de SQL Server afin que les interactions avec la source de données utilisent la bibliothèque réseau de TCP/IP Socket.  
  
### <a name="to-specify-the-tcpip-socket-network-library-on-the-sql-server-computer"></a>Pour spécifier la bibliothèque réseau de TCP/IP Socket sur l’ordinateur SQL Server  
  
### <a name="in-microsoft-sql-server-65"></a>Dans Microsoft SQL Server 6.5 :  
  
1.  Dans le menu Démarrer, pointez sur Programmes, pointez sur Microsoft SQL Server 6.5, puis cliquez sur le programme d’installation de SQL.  
  
2.  Cliquez deux fois sur Continuer.  
  
3.  Dans Microsoft SQL Server-boîte de dialogue Options, sélectionnez la prise en charge du réseau de modification, puis cliquez sur Continuer.  
  
4.  Assurez-vous que la case à cocher Sockets TCP/IP est sélectionné, puis cliquez sur OK.  
  
5.  Cliquez sur Continuer pour terminer et quitter le programme d’installation.  
  
### <a name="in-microsoft-sql-server-70"></a>Dans Microsoft SQL Server 7.0 :  
  
1.  Dans le menu Démarrer, pointez sur Programmes, pointez sur Microsoft SQL Server 7.0, puis cliquez sur utilitaire réseau SQL Server.  
  
2.  Sous l’onglet Général de la boîte de dialogue, cliquez sur Ajouter.  
  
3.  Dans la boîte de dialogue Configuration de la bibliothèque réseau, cliquez sur TCP/IP.  
  
4.  Dans les zones d’adresse de Proxy et un numéro de Port, entrez le port numéro et l’adresse proxy fourni par votre administrateur réseau.  
  
5.  Cliquez sur OK pour terminer et quitter le programme d’installation.  
  
## <a name="configuring-the-web-server-to-use-tcpip-sockets"></a>Configuration du serveur Web pour utiliser des Sockets TCP/IP  
 Il existe deux options de configuration du serveur Web pour utiliser des Sockets TCP/IP. Ce que vous faites dépend de si tous les serveurs SQL sont accessibles à partir du serveur Web, ou uniquement un serveur SQL spécifique est accessible à partir du serveur Web.  
  
 Si tous les serveurs SQL sont accessibles à partir du serveur Web, vous devez exécuter l’utilitaire de Configuration SQL Server Client sur l’ordinateur serveur Web. La procédure suivante modifie la bibliothèque de réseau par défaut pour toutes les connexions SQL Server fait à partir de ce serveur Web IIS pour utiliser la bibliothèque de réseau des Sockets TCP/IP.  
  
### <a name="to-configure-the-web-server-all-sql-servers"></a>Pour configurer le serveur Web (tous les serveurs SQL)  
  
### <a name="for-microsoft-sql-server-65"></a>Pour Microsoft SQL Server 6.5 :  
  
1.  Dans le menu Démarrer, pointez sur Programmes, pointez sur Microsoft SQL Server 6.5, puis cliquez sur utilitaire Configuration du Client SQL.  
  
2.  Cliquez sur l’onglet de la Net-Library.  
  
3.  Dans la zone réseau par défaut, sélectionnez Sockets TCP/IP.  
  
4.  Cliquez sur terminé pour enregistrer les modifications et quitter l’utilitaire.  
  
### <a name="for-microsoft-sql-server-70"></a>Pour Microsoft SQL Server 7.0 :  
  
1.  Dans le menu Démarrer, pointez sur Programmes, pointez sur Microsoft SQL Server 7.0, puis cliquez sur utilitaire réseau du Client.  
  
2.  Cliquez sur l’onglet Général.  
  
3.  Dans la zone de bibliothèque réseau par défaut, cliquez sur TCP/IP.  
  
4.  Cliquez sur OK pour enregistrer les modifications et quitter l’utilitaire.  
  
 Si un serveur SQL spécifique est accessible à partir d’un serveur Web, vous devez exécuter l’utilitaire de Configuration SQL Server Client sur l’ordinateur serveur Web. Pour modifier la bibliothèque réseau pour une connexion SQL Server spécifique, vous devez configurer le logiciel Client de SQL Server sur l’ordinateur serveur Web comme suit.  
  
### <a name="to-configure-the-web-server-a-specific-sql-server"></a>Pour configurer le serveur Web (SQL Server spécifique)  
  
### <a name="for-microsoft-sql-server-65"></a>Pour Microsoft SQL Server 6.5 :  
  
1.  Dans le menu Démarrer, pointez sur Programmes, pointez sur Microsoft SQL Server 6.5, puis cliquez sur utilitaire Configuration du Client SQL.  
  
2.  Cliquez sur l’onglet Avancé.  
  
3.  Dans la zone serveur, tapez le nom du serveur pour vous connecter à l’aide de Sockets TCP/IP.  
  
4.  Dans la zone Nom de la DLL, sélectionnez Sockets TCP/IP.  
  
5.  Cliquez sur Ajouter/modifier. Toutes les sources de données qui pointe vers ce serveur seront désormais utiliser des Sockets TCP/IP.  
  
6.  Cliquez sur terminé.  
  
### <a name="for-microsoft-sql-server-70"></a>Pour Microsoft SQL Server 7.0 :  
  
1.  Dans le menu Démarrer, pointez sur Programmes, pointez sur Microsoft SQL Server 7.0, puis cliquez sur utilitaire de Configuration du Client.  
  
2.  Cliquez sur l’onglet Général.  
  
3.  Cliquez sur Ajouter.  
  
4.  Entrez l’alias du serveur dans la zone d’alias de serveur. Dans la zone de bibliothèques réseau, cliquez sur TCP/IP. Dans la zone de nom d’ordinateur, entrez le nom d’ordinateur de l’ordinateur qui écoute les clients de Sockets TCP/IP. Dans la zone numéro de Port, entrez le port sur lequel écoute le serveur SQL Server.  
  
5.  Cliquez sur OK, puis OK à nouveau pour quitter l’utilitaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base de RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)






















