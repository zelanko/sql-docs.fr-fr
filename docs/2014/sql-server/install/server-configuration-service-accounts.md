---
title: Configuration du serveur - comptes de Service | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- service account configuration, SQL Server
ms.assetid: c283702d-ab20-4bfa-9272-f0c53c31cb9f
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8435b0c677f80bf4f26acd4411d90ab63c7473d1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66092269"
---
# <a name="server-configuration---service-accounts"></a>Configuration du serveur - Comptes de service
  Utilisez la page Configuration du serveur de l'Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour attribuer des comptes de connexion aux services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Les services configurés dans cette page dépendent des fonctionnalités que vous avez sélectionnées.  
  
 Comptes de démarrage utilisés pour démarrer et exécuter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent être des comptes utilisateur de domaine HYPERLINK « ms-help://SQL11_I1033/s11sq_GetStart_I/html/309b9dac-0b3a-4617-85ef-c4519ce9d014.htm » \l « Domain_User », les comptes d’utilisateurs locaux, les comptes de service administrés, les comptes virtuels ou des comptes système intégrés.  
  
## <a name="options"></a>Options  
 Vous pouvez attribuer le même compte de connexion à tous les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou configurer chaque compte de service individuellement. Vous pouvez également spécifier si les services démarrent automatiquement, sont démarrés manuellement ou sont désactivé. Le compte par défaut est recommandé pour la plupart des installations.  
  
 Sous Windows 7 et [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] R2, la plupart des comptes correspondent par défaut à un compte virtuel.  
  
 Si vous configurez des services afin d'utiliser des comptes de domaine, [!INCLUDE[msCoName](../../includes/msconame-md.md)] vous recommande de configurer les comptes de service individuellement afin de fournir des privilèges moindres pour chaque service, où les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disposent des autorisations minimales requises pour effectuer leurs tâches. Pour plus d'informations et les descriptions des types de comptes, consultez [Configure Windows Service Accounts and Permissions](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
 **Configurer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] comptes de service individuellement (recommandé)**  
 Utilisez la grille pour attribuer à chaque service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] un nom d'utilisateur et un mot de passe d'ouverture de session et définir le type de démarrage pour le service. Vous pouvez utiliser des comptes système intégrés, un compte local, un groupe local, un groupe de domaine ou des comptes d'utilisateurs de domaine pour les services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Sélectionnez l'un des services suivants pour en personnaliser les paramètres.  
  
|Sélectionnez ce service|Pour configurer les paramètres d'authentification pour|  
|-------------------------|----------------------------------------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent|Service qui exécute les travaux, analyse [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]et autorise l'automatisation de certaines tâches administratives.<br /><br /> Il n'y a aucun compte d'ouverture de session par défaut pour ce service.<br /><br /> Le type de démarrage par défaut est Manuel.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|Le type de démarrage par défaut est Automatique.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|Le type de démarrage par défaut est Automatique.<br /><br /> Pour le mode intégré SharePoint, vous devez spécifier un compte d'utilisateur de domaine Windows. Le compte que vous spécifiez est utilisé pour le service [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Le compte que vous spécifiez pour l'instance actuelle doit également être utilisé pour toutes les instances [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supplémentaires que vous ajoutez par la suite à la même batterie.|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Les comptes de service sont utilisés pour configurer une connexion à la base de données du serveur de rapports. Choisissez le service réseau intégré si vous souhaitez utiliser les paramètres d'authentification par défaut. Si vous spécifiez un compte d'utilisateur de domaine, assurez-vous d'inscrire un nom principal de service (SPN) pour ce compte si vous utilisez l'authentification Windows sur le serveur de rapports. Pour plus d’informations, consultez [Configure Windows Authentication on the Report Server](../../reporting-services/security/configure-windows-authentication-on-the-report-server.md).<br /><br /> Le type de démarrage par défaut est Automatique.|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] propose un ensemble d’outils graphiques et d’objets programmables permettant de déplacer, de copier et de transformer les données.<br /><br /> Le type de démarrage par défaut est Automatique.|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Client|Compte de service utilisé pour le service Distributed Replay Client.<br /><br /> Fournissez un compte dans lequel exécuter le service Distributed Replay Client. Ce compte doit être différent de celui que vous utilisez pour le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Le type de démarrage par défaut est Manuel.|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller|Compte de service utilisé pour le service Distributed Replay Controller.<br /><br /> Fournissez un compte dans lequel exécuter le service Distributed Replay Controller. Ce compte doit être différent de celui que vous utilisez pour le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Le type de démarrage par défaut est Manuel.|  
|Lanceur de démon de filtre de texte intégral [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|Service qui crée les processus fdhost.exe. Ce service est obligatoire pour héberger les analyseurs lexicaux et filtres qui traitent les données textuelles pour l'indexation de texte intégral.<br /><br /> Si vous fournissez un compte de domaine dans lequel exécuter le service de lancement FDHOST, nous vous recommandons vivement d'utiliser un compte à faibles privilèges. Ce compte doit être différent de celui que vous utilisez pour le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser est le service de résolution des noms qui fournit des informations de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aux ordinateurs clients. Ce service est partagé entre plusieurs instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Le compte d'ouverture de session par défaut est AUTORITE NT\Service local ; il ne peut pas être modifié durant l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Vous pouvez modifier le compte une fois l'installation terminée. Si le type de démarrage n'est pas spécifié pendant l'installation, il est déterminé comme suit :<br /><br /> La valeur Automatique est affectée au démarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser et ce dernier s'exécute dans les scénarios d'installation décrits ci-dessous :<br />-<br />                            Instance de cluster de basculement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<br />-<br />                            Instance nommée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] où est activé le protocole TCP ou celui des canaux nommés<br />-<br />                            Instance nommée du Analysis Server non cluster<br /><br /> Si aucun des scénarios ci-dessus ne s'applique et si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser est déjà installé, l'état actuel de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser est conservé.<br /><br /> La valeur Désactivé est affectée au type de démarrage et ce dernier est arrêté en l'absence d'une version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] plus ancienne avant l'installation.|  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations sur la sécurité pour une installation SQL Server](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
  
