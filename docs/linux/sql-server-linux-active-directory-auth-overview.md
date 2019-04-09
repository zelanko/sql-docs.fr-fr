---
title: Authentification Active Directory pour SQL Server sur Linux
titleSuffix: SQL Server
description: Cet article fournit une vue d’ensemble de l’authentification Active Directory pour SQL Server sur Linux.
author: rothja
ms.date: 04/01/2019
ms.author: jroth
manager: craigg
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux, seodec18
ms.technology: linux
helpviewer_keywords:
- Linux, AAD authentication
ms.openlocfilehash: a4411f8ff8b1eae7fa7a28615e34d0711829d081
ms.sourcegitcommit: aa4f594ec6d3e85d0a1da6e69fa0c2070d42e1d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59241019"
---
# <a name="active-directory-authentication-for-sql-server-on-linux"></a>Authentification Active Directory pour SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Cet article fournit une vue d’ensemble de l’authentification Active Directory (AD) pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur Linux. L’authentification Active Directory est également appelé authentification intégrée dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. 

## <a name="ad-authentication-overview"></a>Vue d’ensemble de l’authentification AD

L’authentification Active Directory permet joints au domaine des clients sur Windows ou Linux pour s’authentifier auprès de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à l’aide de leurs informations d’identification de domaine et le protocole Kerberos.

L’authentification Active Directory présente les avantages suivants sur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] l’authentification :

- Les utilisateurs s’authentifient via l’authentification unique, sans avoir à saisir un mot de passe.   
- En créant des connexions pour les groupes AD, vous pouvez gérer l’accès et les autorisations dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à l’aide des appartenances aux groupes AD.  
- Chaque utilisateur a une identité unique au sein de votre organisation, donc vous n’êtes pas obligé d’effectuer le suivi de qui [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] connexions correspondent aux personnes.   
- Active Directory vous permet d’appliquer une stratégie de mot de passe centralisée au sein de votre organisation.   

## <a name="configuration-steps"></a>Étapes de configuration

Pour pouvoir utiliser l’authentification Active Directory, vous devez disposer d’un contrôleur de domaine Active Directory (Windows) sur votre réseau.

Les détails pour savoir comment configurer l’authentification Active Directory sont fournis dans le didacticiel, [didacticiel : Utilisez l’authentification Active Directory avec SQL Server sur Linux](sql-server-linux-active-directory-authentication.md). La liste suivante fournit un résumé avec un lien vers chaque section dans le didacticiel :

1. [Joindre un ordinateur hôte SQL Server à un domaine Active Directory](sql-server-linux-active-directory-join-domain.md).
1. [Créer un utilisateur AD pour SQL Server et définissez ServicePrincipalName](sql-server-linux-active-directory-authentication.md#createuser).
1. [Configurer le service de SQL Server fichier keytab](sql-server-linux-active-directory-authentication.md#configurekeytab).
1. [Sécuriser le fichier keytab](sql-server-linux-active-directory-authentication.md#securekeytab).
1. [Configurer SQL Server pour utiliser le fichier keytab pour l’authentification Kerberos](sql-server-linux-active-directory-authentication.md#keytabkerberos).
1. [Créer des connexions basées sur Active Directory SQL Server dans Transact-SQL](sql-server-linux-active-directory-authentication.md#createsqllogins).
1. [Se connecter à SQL Server à l’aide de l’authentification AD](sql-server-linux-active-directory-authentication.md#connect).

## <a name="known-issues"></a>Problèmes connus

- À ce stade, la seule méthode d’authentification prise en charge pour le point de terminaison de mise en miroir de base de données est le certificat. La méthode d’authentification WINDOWS sera activée dans une version ultérieure.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur la façon d’implémenter l’authentification Active Directory pour SQL Server sur Linux, consultez [didacticiel : Utilisez l’authentification Active Directory avec SQL Server sur Linux](sql-server-linux-active-directory-authentication.md).
