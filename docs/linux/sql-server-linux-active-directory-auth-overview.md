---
title: L’authentification Active Directory pour SQL Server sur Linux | Microsoft Docs
description: Cet article fournit une vue d’ensemble de l’authentification Active Directory pour SQL Server sur Linux.
author: rothja
ms.date: 02/23/2018
ms.author: jroth
manager: craigg
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
helpviewer_keywords:
- Linux, AAD authentication
ms.openlocfilehash: 9d55275269ee09daf933521330b093a8d98411fd
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39087111"
---
# <a name="active-directory-authentication-for-sql-server-on-linux"></a>Authentification Active Directory pour SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article fournit une vue d’ensemble de l’authentification Active Directory (AD) pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur Linux. L’authentification Active Directory est également appelé authentification intégrée dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. 

## <a name="ad-authentication-overview"></a>Vue d’ensemble de l’authentification AD

L’authentification Active Directory permet joints au domaine des clients sur Windows ou Linux pour s’authentifier auprès de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à l’aide de leurs informations d’identification de domaine et le protocole Kerberos.

L’authentification Active Directory présente les avantages suivants sur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] l’authentification :

- Les utilisateurs s’authentifient via l’authentification unique, sans avoir à saisir un mot de passe.   
- En créant des connexions pour les groupes AD, vous pouvez gérer l’accès et les autorisations dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à l’aide des appartenances aux groupes AD.  
- Chaque utilisateur possède une identité unique dans votre organisation, donc vous n’êtes pas obligé d’effectuer le suivi de quelles connexions [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] correspondent à quelles personnes.   
- Active Directory vous permet d’appliquer une stratégie de mot de passe centralisée au sein de votre organisation.   

## <a name="configuration-steps"></a>Étapes de configuration

Pour pouvoir utiliser l’authentification Active Directory, vous devez disposer d’un contrôleur de domaine Active Directory (Windows) sur votre réseau.

Les détails pour savoir comment configurer l’authentification Active Directory sont fournis dans le didacticiel, [didacticiel : authentification d’utilisation d’Active Directory avec SQL Server sur Linux](sql-server-linux-active-directory-authentication.md). La liste suivante fournit un résumé avec un lien vers chaque section dans le didacticiel :

1. [Joindre un ordinateur hôte SQL Server à un domaine Active Directory](sql-server-linux-active-directory-authentication.md#join).
1. [Créer un utilisateur AD pour SQL Server et définissez ServicePrincipalName](sql-server-linux-active-directory-authentication.md#createuser).
1. [Configurer le service de SQL Server fichier keytab](sql-server-linux-active-directory-authentication.md#configurekeytab).
1. [Créer des connexions basées sur Active Directory SQL Server dans Transact-SQL](sql-server-linux-active-directory-authentication.md#createsqllogins).
1. [Se connecter à SQL Server à l’aide de l’authentification AD](sql-server-linux-active-directory-authentication.md#connect).

## <a name="known-issues"></a>Problèmes connus

- À ce stade, la seule méthode d’authentification prise en charge pour le point de terminaison de mise en miroir de base de données est le certificat. La méthode d’authentification WINDOWS sera activée dans une version ultérieure.
- Outils de AD tiers comme Centrify, Powerbroker, et Vintela ne sont pas pris en charge.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur la façon d’implémenter l’authentification Active Directory pour SQL Server sur Linux, consultez [didacticiel : authentification d’utilisation d’Active Directory avec SQL Server sur Linux](sql-server-linux-active-directory-authentication.md).