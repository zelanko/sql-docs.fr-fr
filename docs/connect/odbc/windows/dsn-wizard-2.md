---
title: Écran 2 (pilote ODBC pour SQL Server) de l’Assistant Source de données | Microsoft Docs
ms.custom: ''
ms.date: 03/21/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
author: MightyPen
ms.author: v-jizho2
manager: jroth
ms.openlocfilehash: 2c41b9215979488cbec9ebda89d98bb0f464d11a
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66797808"
---
# <a name="data-source-wizard-screen-2"></a>Assistant Source de données - Écran 2

Spécifiez la méthode d’authentification et configurez les entrées de client avancé Microsoft SQL Server ainsi que le nom de connexion et le mot de passe utilisés par ODBC Driver for SQL Server pour se connecter à SQL Server lors de la configuration de la source de données.

## <a name="options"></a>Options

### <a name="with-integrated-windows-authentication"></a>Avec l’authentification Windows intégrée

Spécifie que le pilote demande une connexion sécurisée (ou approuvée) à un serveur SQL Server. Si cette option est sélectionnée, SQL Server utilise la sécurité de connexion intégrée pour établir des connexions à l'aide de cette source de données, quel que soit le mode de sécurité de connexion en vigueur au niveau du serveur. Tout ID de connexion ou mot de passe fourni est ignoré. L’administrateur système SQL Server doit avoir associé votre nom d’utilisateur Windows à un ID de connexion SQL Server (par exemple, en utilisant SQL Server Management Studio).

Vous pouvez éventuellement spécifier un nom de principal du service (SPN) pour le serveur.

### <a name="with-active-directory-integrated-authentication"></a>Avec l’authentification intégrée Active Directory

Spécifie que le pilote s’authentifier à SQL Server à l’aide d’Azure Active Directory. Si cette option est sélectionnée, SQL Server utilise la sécurité de connexion intégrée Azure Active Directory pour établir une connexion avec cette source de données, quel que soit le mode de sécurité de connexion en vigueur au niveau du serveur.

### <a name="with-sql-server-authentication"></a>Avec l’authentification SQL Server

Spécifie que le pilote s’authentifier à SQL Server à l’aide d’un ID de connexion et le mot de passe.

### <a name="with-active-directory-password-authentication"></a>Avec l’authentification par mot de passe Active Directory

Spécifie que le pilote s’authentifier à SQL Server à l’aide d’un ID de connexion Azure Active Directory et le mot de passe.

### <a name="with-active-directory-interactive-authentication"></a>Avec l’authentification interactive Active Directory

Spécifie que le pilote s’authentifier à SQL Server à l’aide du mode interactif Azure Active Directory en fournissant l’ID de connexion. Cette opération déclenche la boîte de dialogue invite l’authentification Windows Azure.

### <a name="login-id"></a>Nom d'accès

Spécifie l’ID de connexion le pilote utilise lors de la connexion à SQL Server si **avec l’authentification SQL Server à l’aide d’un ID de connexion et un mot de passe entré par l’utilisateur** ou **authentification avec Active Directory mot de passe à l’aide d’un ID de connexion et le mot de passe entré par l’utilisateur** ou **l’authentification avec Active Directory Interactive à l’aide d’un ID de connexion entré par l’utilisateur** est sélectionné. Cela s'applique uniquement à la connexion établie pour déterminer les paramètres serveur par défaut, pas aux connexions établies ultérieurement à l'aide de la source de données, après sa création.

### <a name="password"></a>Mot de passe

Spécifie le mot de passe que le pilote utilise lors de la connexion à SQL Server si **avec l’authentification SQL Server à l’aide d’un ID de connexion et un mot de passe entré par l’utilisateur** ou **authentification avec Active Directory mot de passe à l’aide d’un ID de connexion et le mot de passe entré par l’utilisateur** est sélectionné. Cela s'applique uniquement à la connexion établie pour déterminer les paramètres serveur par défaut, pas aux connexions établies ultérieurement à l'aide de la nouvelle source de données.

Les deux le **ID de connexion** et **mot de passe** sont désactivées si **l’authentification avec intégré Windows** ou **avec Active Directory intégré authentification** est sélectionné.

### <a name="next"></a>Suivant

Passe à l’écran suivant de l’Assistant.

### <a name="back"></a>Précédent

Retourne à l’écran précédent de l’Assistant.

## <a name="next-steps"></a>Étapes suivantes

[Assistant Source de données, écran 1](../../../connect/odbc/windows/dsn-wizard-1.md)

[Assistant Source de données, écran 3](../../../connect/odbc/windows/dsn-wizard-3.md)

