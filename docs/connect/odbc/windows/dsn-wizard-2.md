---
title: Assistant source de données-écran 2 (pilote ODBC pour SQL Server) | Microsoft Docs
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
ms.openlocfilehash: c997dd30b6d1e9844843ff4fa626c46b42fed463
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67936572"
---
# <a name="data-source-wizard-screen-2"></a>Assistant Source de données - Écran 2

Spécifiez la méthode d’authentification et configurez les entrées de client avancé Microsoft SQL Server ainsi que le nom de connexion et le mot de passe utilisés par ODBC Driver for SQL Server pour se connecter à SQL Server lors de la configuration de la source de données.

## <a name="options"></a>Options

### <a name="with-integrated-windows-authentication"></a>Avec l’authentification Windows intégrée

Spécifie que le pilote demande une connexion sécurisée (ou approuvée) à un SQL Server. Si cette option est sélectionnée, SQL Server utilise la sécurité de connexion intégrée pour établir des connexions à l'aide de cette source de données, quel que soit le mode de sécurité de connexion en vigueur au niveau du serveur. Tout ID de connexion ou mot de passe fourni est ignoré. Le SQL Server administrateur système doit avoir associé votre compte de connexion Windows à un ID de connexion SQL Server (par exemple, en utilisant SQL Server Management Studio).

Vous pouvez éventuellement spécifier un nom de principal du service (SPN) pour le serveur.

### <a name="with-active-directory-integrated-authentication"></a>Avec l’authentification intégrée Active Directory

Spécifie que le pilote s’authentifie auprès d’SQL Server à l’aide de Azure Active Directory. Si cette option est sélectionnée, SQL Server utilise la sécurité de connexion intégrée Azure Active Directory pour établir une connexion avec cette source de données, quel que soit le mode de sécurité de connexion en vigueur au niveau du serveur.

### <a name="with-sql-server-authentication"></a>Avec l’authentification SQL Server

Spécifie que le pilote s’authentifie auprès d’SQL Server à l’aide d’un ID de connexion et d’un mot de passe.

### <a name="with-active-directory-password-authentication"></a>Avec l’authentification par mot de passe Active Directory

Spécifie que le pilote s’authentifie auprès d’SQL Server à l’aide d’un ID de connexion et d’un mot de passe Azure Active Directory.

### <a name="with-active-directory-interactive-authentication"></a>Avec l’authentification interactive Active Directory

Spécifie que le pilote s’authentifie sur SQL Server à l’aide du mode interactif Azure Active Directory en fournissant l’ID de connexion. La boîte de dialogue invite d’authentification Windows Azure s’affiche.

### <a name="login-id"></a>Nom d'accès

Spécifie l’ID de connexion utilisé par le pilote lors de la connexion à SQL Server si **avec l’authentification SQL Server à l’aide d’un ID de connexion et d’un mot de passe entrés par l’utilisateur** ou **avec l’authentification par Active Directory mot de passe à l’aide d’un ID de connexion et d’un mot** ou **avec Active Directory authentification interactive à l’aide d’un ID de connexion entré par l’utilisateur** est sélectionné. Cela s'applique uniquement à la connexion établie pour déterminer les paramètres serveur par défaut, pas aux connexions établies ultérieurement à l'aide de la source de données, après sa création.

### <a name="password"></a>Mot de passe

Spécifie le mot de passe utilisé par le pilote lors de la connexion à SQL Server si **avec l’authentification SQL Server à l’aide d’un ID de connexion et d’un mot de passe entrés par l’utilisateur** ou avec l’authentification par Active Directory mot de passe avec **un ID de connexion et un mot de passe entrés** est sélectionné. Cela s'applique uniquement à la connexion établie pour déterminer les paramètres serveur par défaut, pas aux connexions établies ultérieurement à l'aide de la nouvelle source de données.

Les zones **ID de connexion** et **mot de passe** sont désactivées si l’option **avec l’authentification Windows intégrée** ou **avec l’authentification intégrée Active Directory** est sélectionnée.

### <a name="next"></a>Suivant

Passe à l’écran suivant de l’Assistant.

### <a name="back"></a>Précédent

Revient à l’écran précédent de l’Assistant.

## <a name="next-steps"></a>Étapes suivantes

[Assistant Source de données, écran 1](../../../connect/odbc/windows/dsn-wizard-1.md)

[Assistant Source de données, écran 3](../../../connect/odbc/windows/dsn-wizard-3.md)

