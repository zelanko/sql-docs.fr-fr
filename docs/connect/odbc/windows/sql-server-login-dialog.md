---
title: Boîte de dialogue de connexion SQL Server (ODBC) | Microsoft Docs
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
ms.openlocfilehash: 2d7cf1f31ce5cf42b9c2e4c7b72938b8def2ed4f
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66797740"
---
# <a name="sql-server-login-dialog-box-odbc"></a>Compte de connexion SQL Server, boîte de dialogue (ODBC)

Lorsque vous appelez une connexion ODBC sans spécifier suffisamment d’informations pour que le pilote ODBC puisse se connecter à un serveur SQL Server, il affiche la boîte de dialogue **Connexion à SQL Server**.

## <a name="options"></a>Options

### <a name="server"></a>Serveur

Le nom d’une instance de SQL Server sur votre réseau. Tapez le nom serveur\instance dans la zone **Serveur**, ou sélectionnez-en un dans la liste. Vous pouvez si vous le souhaitez créer un alias de serveur sur l’ordinateur client avec le **Gestionnaire de configuration SQL Server** et taper ce nom dans la zone **Serveur**.

Vous pouvez entrer "(local)" lorsque vous utilisez le même ordinateur que SQL Server. Vous pouvez alors vous connecter à une instance locale de SQL Server, même s’il s’agit d’une version de SQL Server qui n’est pas en réseau.

Pour plus d’informations sur les noms de serveurs de différents types de réseaux, consultez la documentation d’installation de SQL Server dans la Documentation en ligne de SQL Server.

### <a name="authentication-mode"></a>Mode d'authentification

Sélectionne le mode d’authentification à partir d’une des opérations suivantes :
- **SQL Server** avec l’ID de connexion et mot de passe
- **Windows intégrée** authentification à l’aide d’actuellement connecté en compte de l’utilisateur
- **Mot de passe Active Directory** avec l’ID de connexion et mot de passe
- **Intégrée à Active Directory** authentification à l’aide d’actuellement connecté en compte de l’utilisateur
- Authentification **interactive Active Directory** avec ID de connexion

Consultez [Data Source Assistant écran 2](../../../connect/odbc/windows/dsn-wizard-2.md) pour plus d’informations sur les modes d’authentification.

### <a name="server-spn"></a>SPN du serveur

Si vous utilisez une connexion approuvée, vous pouvez spécifier un nom de principal de service (SPN) pour le serveur.

### <a name="login-id"></a>Nom d'accès

Spécifie l’ID de connexion SQL Server ou Azure Active Directory à utiliser pour la connexion si **Mode d’authentification** a la valeur **SQL Server** ou **mot de passe Active Directory** ou **Active Directory Interactive**. Sinon, le **ID de connexion** zone est désactivée.

### <a name="password"></a>Mot de passe

Spécifie le mot de passe pour l’ID de connexion SQL Server ou Azure Active Directory est utilisé pour la connexion si **Mode d’authentification** a la valeur **SQL Server** ou **Directory mot de passe Active**. Sinon, le **mot de passe** zone est désactivée.

### <a name="options"></a>Options

Affiche ou masque le groupe **Options**. Le bouton **Options** est activé si **Serveur** a une valeur.

### <a name="change-password"></a>Modification du mot de passe

Lorsque cette zone est sélectionnée, affiche les zones **Nouveau mot de passe** et **Confirmer le nouveau mot de passe**.

### <a name="new-password"></a>Nouveau mot de passe

Spécifie le nouveau mot de passe.

### <a name="confirm-new-password"></a>Confirmer le nouveau mot de passe

Spécifie une deuxième fois le nouveau mot de passe, à des fins de confirmation.

### <a name="database"></a>Base de données

Spécifie la base de données par défaut à utiliser sur la connexion. Ce paramètre remplace la base de données par défaut spécifiée pour le nom de connexion sur le serveur. Si aucune base de données n'est spécifiée, la connexion utilise la base de données par défaut spécifiée pour le nom de connexion sur le serveur.

### <a name="mirror-server"></a>Serveur miroir

Indique le nom du partenaire de basculement de la base de données à mettre en miroir.

### <a name="mirror-spn"></a>SPN miroir

Facultativement, vous pouvez spécifier un SPN pour le serveur miroir. Le SPN du serveur miroir est utilisé pour l'authentification mutuelle entre client et serveur.

### <a name="language"></a>Langue

Spécifie la langue nationale à utiliser pour les messages système SQL Server. La langue en question doit être installée sur l’ordinateur qui exécute SQL Server. Ce paramètre remplace la langue par défaut spécifiée pour le nom de connexion sur le serveur. Si aucune langue n'est spécifiée, la connexion utilise la langue par défaut spécifiée pour le nom de connexion sur le serveur.

### <a name="application-name"></a>Application Name

(Facultatif) Spécifie le nom de l’application à stocker dans la colonne **program_name** dans la ligne de cette connexion dans **sys.sysprocesses**.

### <a name="workstation-id"></a>ID Station de travail

(Facultatif) Spécifie l’ID de station de travail à stocker dans la colonne **hostname** dans la ligne de cette connexion dans **sys.sysprocesses**.

### <a name="use-strong-encryption-for-data"></a>Utiliser le chiffrement renforcé pour les données

Lorsque sélectionné, les données qui sont transmises via la connexion seront chiffrées. Les noms de connexion sont chiffrés par défaut, même si la case à cocher est désactivée.

### <a name="trust-server-certificate"></a>Faire confiance au certificat de serveur

Cette option est applicable uniquement lorsque **utiliser un chiffrement renforcé pour les données** est activé. Quand sélectionné, il est possible que le certificat du serveur n’est pas validé pour avoir le nom d’hôte correct du serveur et être émis par une autorité de certification approuvée.

## <a name="see-also"></a>Voir aussi

[Pilote Microsoft ODBC pour SQL Server sur Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)
