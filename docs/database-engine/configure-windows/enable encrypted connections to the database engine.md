---
title: "Activer les connexions chiffr&#233;es dans le moteur de base de donn&#233;es (Gestionnaire de configuration SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "connexions [SQL Server], chiffrées"
  - "SSL [SQL Server]"
  - "SSL (Secure Sockets Layer)"
  - "chiffrement [SQL Server], connexions"
  - "cryptographie [SQL Server], connexions"
  - "certificats [SQL Server], installation"
  - "demandes de connexions chiffrées"
  - "installation des certificats"
  - "sécurité [SQL Server], chiffrement"
ms.assetid: e1e55519-97ec-4404-81ef-881da3b42006
caps.latest.revision: 48
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Activer les connexions chiffr&#233;es dans le moteur de base de donn&#233;es (Gestionnaire de configuration SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Cette rubrique explique comment activer les connexions chiffrées d’une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] en spécifiant un certificat pour le [!INCLUDE[ssDE](../../includes/ssde-md.md)] à l’aide du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . L'ordinateur serveur doit être accompagné (approvisionné) d'un certificat et vous devez configurer l'ordinateur client pour permettre l'approbation de l'autorité racine du certificat. L'approvisionnement désigne le processus d'installation d'un certificat par son importation dans Windows.  
  
 Le certificat doit être émis pour l' **authentification serveur**. Le nom du certificat doit être le nom de domaine complet de l'ordinateur.  
  
 Les certificats sont stockés localement pour les utilisateurs de l'ordinateur. Pour installer un certificat et l'utiliser dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez exécuter le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sous le même compte d'utilisateur que le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , à moins que le service ne s'exécute en tant que compte LocalSystem, NetworkService ou LocalService, auquel cas vous pouvez utiliser un compte d'administrateur.  
  
 Le client doit être en mesure de vérifier la propriété du certificat employé par le serveur. Si le client dispose du certificat de clé publique de l'autorité de certification qui a signé le certificat de serveur, aucune configuration supplémentaire n'est requise. [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows comprend les certificats de clé publique d'un grand nombre d'autorités de certification. Si le certificat de serveur a été signé par une autorité de certification publique ou privée pour laquelle le client ne dispose pas de certificat de clé publique, vous devez installer le certificat de clé publique de l'autorité de certification ayant signé le certificat de serveur.  
  
> [!NOTE]  
>  Pour utiliser le chiffrement à l'aide d'un cluster de basculement, installez le certificat du serveur avec le nom DNS complet du serveur virtuel sur tous les nœuds du cluster de basculement. Si, par exemple, vous disposez d’un cluster à deux nœuds nommés test1.*\<votre_société>*.com et test2.*\<votre_société>*.com, ainsi que d’un serveur virtuel nommé virtsql, vous devez installer un certificat pour virtsql.*\<votre_société>*.com sur les deux nœuds. Vous pouvez affecter la valeur **ForceEncryption**(Oui) à l’option **ForceEncryption**.  

> [!NOTE]
> Si vous créez des connexions chiffrées entre un indexeur de la Recherche Azure et SQL Server sur une machine virtuelle Azure, consultez [Configurer une connexion à partir d’un indexeur de la Recherche Azure à SQL Server sur une machine virtuelle Azure](https://azure.microsoft.com/documentation/articles/search-howto-connecting-azure-sql-iaas-to-azure-search-using-indexers/). 
  
 
##  <a name="SSMSProcedure"></a>  
  
###  <a name="Provision"></a> Pour installer un certificat sur le serveur  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**puis, dans la zone **Ouvrir** , tapez **MMC** et cliquez sur **OK**.  
  
2.  Dans la console MMC, dans le menu **Fichier**, cliquez sur **Ajouter/Supprimer un composant logiciel enfichable**.  
  
3.  Dans la boîte de dialogue **Ajouter/Supprimer un composant logiciel enfichable**, cliquez sur **Ajouter**.  
  
4.  Dans la boîte de dialogue **Ajout d’un composant logiciel enfichable autonome**, cliquez sur **Certificats**, puis sur **Ajouter**.  
  
5.  Dans la boîte de dialogue **Composant logiciel enfichable Certificats**, cliquez sur **Compte d’ordinateur**, puis sur **Terminer**.  
  
6.  Dans la boîte de dialogue **Ajout d’un composant logiciel enfichable autonome**, cliquez sur **Fermer**.  
  
7.  Dans la boîte de dialogue **Ajouter/Supprimer un composant logiciel enfichable**, cliquez sur **OK**.  
  
8.  Dans le composant logiciel enfichable **Certificats**, développez **Certificats**, **Personnel**, cliquez avec le bouton droit sur **Certificats**, pointez sur **Toutes les tâches**, puis cliquez sur **Importer**.  

9. Cliquez avec le bouton droit sur le certificat importé, pointez sur **Toutes les tâches**, puis cliquez sur **Gérer les clés privées**. Dans la boîte de dialogue **Sécurité**, ajoutez l’autorisation de lecture pour le compte d’utilisateur utilisé par le compte de service SQL Server.  
  
10. Remplissez les informations dans l' **Assistant Importation de certificat**afin d'ajouter un certificat à l'ordinateur, puis fermez la console MMC. Pour plus d'informations sur l'ajout d'un certificat à un ordinateur, consultez la documentation Windows.  
  
###  <a name="Export"></a> Pour exporter le certificat de serveur  
  
1.  Dans le composant logiciel enfichable **Certificats**, recherchez le certificat dans le dossier **Certificats** / **Personnel**, cliquez avec le bouton droit sur **Certificat**, pointez sur **Toutes les tâches**, puis cliquez sur **Exporter**.  
  
2.  Suivez les étapes de l' **Assistant d'exportation de certificats**en stockant le fichier de certificat à un emplacement approprié.  
  
###  <a name="ConfigureServerConnections"></a> Pour configurer le serveur afin qu'il accepte les connexions chiffrées  
  
1.  Dans le **Gestionnaire de configuration SQL Server**, développez **Configuration du réseau SQL Server**, cliquez avec le bouton droit sur **Protocoles pour** *\<instance de serveur>*, puis sélectionnez **Propriétés**.  
  
2.  Dans la boîte de dialogue **Propriétés de** **Protocoles pour***\<nom_instance>*, sous l’onglet **Certificat**, sélectionnez le certificat voulu dans la liste déroulante de la zone **Certificat**, puis cliquez sur **OK**.  
  
3.  Sur l'onglet **Indicateurs** , dans la zone **ForceEncryption** , sélectionnez **Oui**, puis cliquez sur **OK** pour fermer la boîte de dialogue.  
  
4.  Redémarrez le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
###  <a name="ConfigureClientConnections"></a> Pour configurer le client afin qu'il demande l'établissement de connexions chiffrées  
  
1.  Copiez le certificat d'origine ou le fichier de certificat exporté sur l'ordinateur client.  
  
2.  Sur l’ordinateur client, utilisez le composant logiciel enfichable **Certificats** pour installer le certificat racine ou le fichier de certificat exporté.  
  
3.  Dans le volet de la console, cliquez avec le bouton droit sur **Configuration de SQL Server Native Client**, puis cliquez sur **Propriétés**.  
  
4.  Sur la page **Indicateurs** , dans la zone **Forcer le chiffrement du protocole** , cliquez sur **Oui**.  
  
###  <a name="EncryptConnection"></a> Pour chiffrer une connexion dans SQL Server Management Studio  
  
1.  Dans la barre d'outils de l'Explorateur d'objets, cliquez sur **Connecter**, puis sur **Moteur de base de données**.  
  
2.  Dans la boîte de dialogue **Se connecter au serveur** , fournissez les informations de connexion, puis cliquez sur **Options**.  
  
3.  Sous l'onglet **Propriétés de connexion** , cliquez sur **Chiffrer la connexion**.  
  
## Voir aussi

[Prise en charge de TLS 1.2 pour Microsoft SQL Server](https://support.microsoft.com/kb/3135244)  
