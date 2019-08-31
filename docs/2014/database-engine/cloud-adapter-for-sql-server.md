---
title: adaptateur cloud pour SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Cloud adapter
- Deploy to Azure
ms.assetid: 82ed0d0f-952d-4d49-aa36-3855a3ca9877
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bf57adb31330f5b0c0f18fbcccd4d71f47d3c933
ms.sourcegitcommit: 3b1f873f02af8f4e89facc7b25f8993f535061c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70176016"
---
# <a name="cloud-adapter-for-sql-server"></a>Adaptateur de cloud pour SQL Server
  Le service adaptateur Cloud est créé dans le cadre [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] de l’approvisionnement sur une machine virtuelle Azure. Il génère un certificat SSL auto-signé dans le cadre de sa première exécution, puis s’exécute en tant que compte **Système local** . Il génère un fichier de configuration utilisé pour sa configuration. L'adaptateur de cloud crée également une règle de Pare-feu Windows pour autoriser les connexions TCP entrantes sur le port 11435 par défaut.  
  
 L'adaptateur de cloud est un service sans état et synchrone qui reçoit les messages de l'instance sur site de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Lorsque le service Adaptateur de cloud est arrêté, il arrête l'adaptateur de cloud d'accès à distance, dissocie le certificat SSL et désactive la règle de Pare-feu Windows.  
  
## <a name="cloud-adapter-requirements"></a>Configuration requise pour l'adaptateur de cloud  
 Notez la configuration requise pour installer, activer, puis exécuter l'adaptateur de cloud pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:  
  
-   L'adaptateur de cloud est pris en charge par [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012 et les versions ultérieures. Sur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012, l'adaptateur de cloud pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] nécessite SQL Management Objects pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2012.  
  
-   Le service Web Adaptateur de cloud s'exécute en tant que compte **Système local** et vérifie les informations d'identification du client avant d'exécuter les tâches. Les informations d’identification fournies par le client doivent appartenir au compte d’utilisation qui est membre du groupe **administrateurs** local sur l’ordinateur distant.  
  
-   L'adaptateur de cloud prend uniquement en charge l'Authentification [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
-   L'adaptateur de cloud utilise le compte d'administrateur local d'ordinateur virtuel pour exécuter des commandes sur l'ordinateur local, et non pas un compte d'administrateur système.  
  
-   L'adaptateur cloud écoute sur le protocole TCP/IP. Le port par défaut est 11435.  
  
-   L'adaptateur de cloud doit disposer d'autorisations pour créer et modifier des règles de Pare-feu Windows.  
  
## <a name="cloud-adapter-configuration-settings"></a>Paramètres de configuration de l'adaptateur de cloud  
 Utilisez les informations de configuration d'adaptateur de cloud suivantes pour modifier les paramètres d'un adaptateur de cloud.  
  
-   **Chemin d’accès par défaut pour le fichier de configuration** -C:\Program Files\Microsoft SQL Server\120\Tools\CloudAdapter\  
  
-   **Paramètres du fichier de configuration** -  
  
    -   \<configuration>  
  
        -   \<appSettings>  
  
            -   \<add key="WebServicePort" value="" />  
  
            -   \<add key="WebServiceCertificate" value="GUID" />  
  
            -   \<add key="ExposeExceptionDetails" value="true" />  
  
        -   \</appSettings>  
  
    -   \</configuration>  
  
-   **Détails du certificat** : le certificat a les valeurs suivantes:  
  
    -   Subject-"CN = CloudAdapter\<vmname >, DC = SQL Server, DC = Microsoft"  
  
    -   Le certificat doit disposer uniquement de l'utilisation améliorée de la clé d'authentification serveur activée.  
  
    -   La longueur de la clé de certificat est 2048.  
  
 **Valeurs du fichier de configuration**:  
  
|Paramètre|Valeurs|Par défaut|Commentaires|  
|-------------|------------|-------------|--------------|  
|WebServicePort|1-65535|11435|Si ce paramètre n'est pas spécifié, utilisez 11435.|  
|WebServiceCertificate|Thumbprint|Empty|Si ce paramètre est vide, un nouveau certificat auto-signé est généré.|  
|ExposeExceptionDetails|True/False|False||  
  
## <a name="cloud-adapter-troubleshooting"></a>Dépannage de l'adaptateur de cloud  
 Utilisez les informations suivantes pour dépanner l'adaptateur de cloud pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:  
  
-   **Gestion des erreurs et journalisation** -les erreurs et les messages d’État sont écrits dans le journal des événements de l’application.  
  
-   **Traçage, événements** -tous les événements sont écrits dans le journal des événements de l’application.  
  
-   **Contrôle, configuration** : utilisez le fichier de configuration situé dans:  C:\Program Files\Microsoft SQL Server\120\Tools\CloudAdapter\\.  
  
|Error|ID d'erreur|Cause|Résolution :|  
|-----------|--------------|-----------|----------------|  
|Une exception s'est produite lors de l'ajout du certificat dans le magasin de certificats. [Texte de l'exception].|45560|Autorisations dans le magasin de certificats de l'ordinateur|Vérifiez que le service Adaptateur de cloud dispose des autorisations nécessaires pour ajouter des certificats dans le magasin de certificats de l'ordinateur.|  
|Une exception s'est produite lors de la configuration de la liaison SSL du port {numéro de port} et du certificat {Thumbprint}. {Exception}.|45561|Une autre application a déjà utilisé le port ou lié un certificat à celui-ci.|Supprimez les liaisons existantes ou modifiez le port de l'adaptateur de cloud dans le fichier de configuration.|  
|Certificat SSL introuvable [{Thumbprint}] dans le magasin de certificats.|45564|L'empreinte numérique de certificat est dans le fichier de configuration, mais le magasin de certificats personnel pour le service ne contient pas de certificat.<br /><br /> Autorisations insuffisantes.|Vérifiez que le certificat se trouve dans le magasin de certificats personnel pour le service.<br /><br /> Vérifiez que le service dispose des autorisations appropriées pour le magasin.|  
|Échec du démarrage du service Web. [Texte de l'exception].|45570|Décrit dans l'exception.|Activez ExposeExceptionDetails et utilisez les informations étendues de l'exception.|  
|Le certificat [{Thumbprint}] a expiré.|45565|Certificat arrivé à expiration référencé dans le fichier de configuration.|Ajoutez un certificat valide et mettez à jour le fichier de configuration avec son empreinte numérique.|  
|Erreur du service Web {0}:.|45571|Décrit dans l'exception.|Activez ExposeExceptionDetails et utilisez les informations étendues de l'exception.|  
  
## <a name="see-also"></a>Voir aussi  
 [Déployer une base de données SQL Server sur une machine virtuelle Microsoft Azure](../relational-databases/databases/deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine.md)  
  
  
