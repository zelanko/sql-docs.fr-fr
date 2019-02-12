---
title: Enregistrer un nom de principal du service (SPN) pour un serveur de rapports | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: dda91d4f-77cc-4898-ad03-810ece5f8e74
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: ea63ef515b1caa524ebc72a87996d1d1d610d63a
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56023450"
---
# <a name="register-a-service-principal-name-spn-for-a-report-server"></a>Inscrire un nom de principal du service (SPN) pour un serveur de rapports
  Si vous déployez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] dans un réseau qui utilise le protocole Kerberos pour l'authentification mutuelle, vous devez créer un nom de principal du service (SPN) pour le service Report Server, si vous le configurez pour s'exécuter en tant que compte d'utilisateur de domaine.  
  
## <a name="about-spns"></a>À propos des noms principaux de service  
 Un nom principal de service est un identificateur unique pour un service sur un réseau qui utilise l'authentification Kerberos. Il est composé d'une classe de service, d'un nom d'hôte et d'un port. Sur un réseau qui utilise l'authentification Kerberos, un nom principal de service pour le serveur doit être inscrit sous un compte d'ordinateur prédéfini (tel que NetworkService ou LocalSystem) ou un compte d'utilisateur. Les noms principaux de service sont enregistrés automatiquement pour les comptes intégrés. Toutefois, lorsque vous exécutez un service sous un compte d'utilisateur de domaine, vous devez inscrire manuellement le nom principal de service pour le compte que vous souhaitez utiliser.  
  
 Pour créer un SPN, vous pouvez utiliser l’utilitaire de ligne de commande **SetSPN** . Pour plus d'informations, consultez les documents suivants :  
  
-   [Setspn](https://technet.microsoft.com/library/cc731241\(WS.10\).aspx) (https://technet.microsoft.com/library/cc731241(WS.10).aspx).  
  
-   [Noms de principaux du service (SPN), syntaxe SetSPN (Setspn.exe)](https://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx) (https://social.technet.microsoft.com/wiki/contents/articles/717.service-principal-names-spns-setspn-syntax-setspn-exe.aspx).  
  
 Vous devez être administrateur de domaine pour exécuter l'utilitaire sur le contrôleur de domaine.  
  
## <a name="syntax"></a>Syntaxe  
 La syntaxe de commande pour utiliser l'utilitaire SetSPN en vue de créer un SPN pour le serveur de rapports ressemble à ce qui suit :  
  
```  
Setspn -s http/<computername>.<domainname>:<port> <domain-user-account>  
```  
  
 **SetSPN** est disponible dans Windows Server. L'argument `-s` ajoute un SPN après avoir vérifié qu'aucun doublon n'existe. **REMARQUE** -s est disponible dans Windows Server depuis Windows Server 2008.  
  
 `HTTP` est la classe de service. Le service Web Report Server s'exécute dans HTTP.SYS. L'une des conséquences de la création d'un nom principal de service pour HTTP est que des tickets seront accordés à toutes les applications Web sur le même ordinateur qui s'exécutent dans HTTP.SYS (y compris les applications hébergées dans les services Internet (IIS)) en fonction du compte d'utilisateur de domaine. Si ces services s'exécutent sous un compte différent, les demandes d'authentification échouent. Pour éviter ce problème, assurez-vous de configurer toutes les applications HTTP pour qu'elles s'exécutent sous le même compte ou envisagez la création d'en-têtes d'hôtes pour chaque application puis la création de noms principaux de service distincts pour chaque en-tête d'hôte. Lorsque vous configurez des en-tête de l'hôte, les modifications de DNS sont requises indépendamment de la configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Les valeurs que vous spécifiez pour \<*nom_ordinateur*>, \<*nom_domaine*> et \<*port*> permettent d’identifier l’adresse réseau unique de l’ordinateur qui héberge le serveur de rapports. Ce peut être un nom d'hôte local ou un nom de domaine complet (FQDN). Si vous n’avez qu’un seul domaine et que vous utilisez le port 80, vous n’avez pas besoin de spécifier les valeurs \<*nom_domaine*> et \<*port*> dans votre ligne de commande. <\<*compte-d’utilisateur-de-domaine*> est le compte d’utilisateur sous lequel le service Report Server s’exécute et pour lequel le SPN doit être inscrit.  
  
## <a name="register-an-spn-for-domain-user-account"></a>Inscrire un SPN pour un compte d'utilisateur de domaine  
  
#### <a name="to-register-an-spn-for-a-report-server-service-running-as-a-domain-user"></a>Pour inscrire un SPN pour un service Report Server qui s'exécute en tant qu'utilisateur de domaine  
  
1.  Installez [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et configurez le service Report Server pour qu’il s’exécute en tant que compte d’utilisateur de domaine. Notez que les utilisateurs ne seront pas en mesure de se connecter au serveur de rapports tant que vous n'aurez pas terminé les étapes suivantes.  
  
2.  Ouvrez une session sur le contrôleur de domaine en tant qu'administrateur de domaine.  
  
3.  Ouvrez une fenêtre d'invite de commandes.  
  
4.  Copiez la commande suivante, en remplaçant les valeurs d'espaces réservés par des valeurs réelles valides pour votre réseau :  
  
    ```  
    Setspn -s http/<computer-name>.<domain-name>:<port> <domain-user-account>  
    ```  
  
     Par exemple : `Setspn -s http/MyReportServer.MyDomain.com:80 MyDomainUser`  
  
5.  Exécutez la commande.  
  
6.  Ouvrez le fichier **RsReportServer.config** et recherchez la section `<AuthenticationTypes>` .  
  
7.  Ajoutez `<RSWindowsNegotiate/>` comme première entrée de cette section pour activer NTLM.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer un compte de service &#40;Gestionnaire de configuration de SSR&#41;](../../sql-server/install/configure-a-service-account-ssrs-configuration-manager.md)   
 [Configurer le compte de service Report Server &#40;Gestionnaire de configuration de SSRS&#41;](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Gérer un serveur de rapports Reporting Services en mode natif](manage-a-reporting-services-native-mode-report-server.md)  
  
  
