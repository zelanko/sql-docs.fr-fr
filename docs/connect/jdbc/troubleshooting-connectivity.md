---
title: Résoudre les problèmes de connectivité | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: bfba0b49-2e1f-411d-a625-d25fad9ea12d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0ef0a0e1a261996c71b3b75add30ee2f28899484
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928116"
---
# <a name="troubleshooting-connectivity"></a>Résoudre les problèmes de connectivité
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] nécessite l’installation et l’exécution du protocole TCP/IP pour pouvoir communiquer avec votre base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez utiliser le gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour vérifier quels sont les protocoles de bibliothèque réseau installés.  
  
 Une tentative de connexion à la base de données peut échouer pour plusieurs raisons. Parmi ces raisons :  
  
-   TCP/IP n’est pas activé pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ou le serveur ou le numéro de port spécifié est incorrect. Vérifiez que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] écoute avec TCP/IP sur le serveur et le port spécifiés. Cela peut être rapporté avec une exception telle que : « Échec de la connexion. La connexion TCP/IP à l'hôte a échoué. » Cela indique l'une des raisons suivantes :  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installé, mais TCP/IP n’a pas été installé en tant que protocole réseau pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de l’utilitaire réseau [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ou du gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et ultérieur.  
  
    -   Le protocole TCP/IP est installé en tant que protocole [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mais il n’écoute pas sur le port spécifié dans l’URL de connexion de JDBC. Le port par défaut est 1433, mais [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut être configuré lors de l’installation du produit pour écouter sur n’importe quel port. Vérifiez que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] écoute sur le port 1433. Autrement, si le port a été modifié, assurez-vous que celui spécifié dans l'URL de connexion de JDBC correspond au port modifié. Pour plus d’informations sur les URL de connexion de JDBC, consultez [Générer l’URL de connexion](../../connect/jdbc/building-the-connection-url.md).  
  
    -   L’adresse de l’ordinateur spécifiée dans l’URL de connexion de JDBC ne renvoie pas à un serveur sur lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installé et démarré.  
  
    -   L’opération de mise en réseau de TCP/IP entre le client et le serveur exécutant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est inexploitable. Vous pouvez vérifier la connectivité TCP/IP à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] via telnet. Par exemple, à l’invite de commande, entrez `telnet 192.168.0.0 1433`, où 192.168.0.0 est l’adresse de l’ordinateur qui exécute [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et 1433 est le port sur lequel s’effectue l’écoute. Si vous recevez un message indiquant « Telnet ne peut pas se connecter », cela signifie que TCP/IP n’écoute pas sur ce port pour des connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Utilisez l’utilitaire réseau [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] ou le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et ultérieur pour vérifier que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré de façon à utiliser TCP/IP sur le port 1433.  
  
    -   Le port utilisé par le serveur n'a pas été ouvert dans le pare-feu. Ceci comprend le port utilisé par le serveur ou éventuellement, le port associé à une instance nommée du serveur.  
  
-   Le nom de base de données spécifié est incorrect. Vérifiez que vous vous connectez à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] existante.  
  
-   Le nom d'utilisateur ou le mot de passe est incorrect. Assurez-vous que vous disposez des valeurs correctes.  
  
-   Quand vous utilisez l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le pilote JDBC nécessite que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] soit installé avec l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ce qui n’est pas le paramètre par défaut. Veillez à activer cette option quand vous installez ou que vous configurez votre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Diagnostic de problèmes avec le pilote JDBC](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)   
 [Connexion à SQL Server avec le pilote JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  
