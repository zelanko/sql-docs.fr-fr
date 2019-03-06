---
title: Universal Data Link (UDL) Configuration | Microsoft Docs
description: Configuration UDL (Data Link) universelle à l’aide du pilote Microsoft OLE DB pour SQL Server
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
ms.author: v-beaziz
author: bazizi
ms.openlocfilehash: e198f561fd4f6bcec390ef8632c1cdc96f2810d6
ms.sourcegitcommit: 958cffe9288cfe281280544b763c542ca4025684
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56744819"
---
# <a name="universal-data-link-udl-configuration"></a>Configuration universelle de UDL (Data Link)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

## <a name="connection-tab"></a>Onglet Connexion
Utilisez l’onglet connexion pour spécifier comment vous connecter à vos données en utilisant le pilote Microsoft OLE DB pour SQL Server.

![Capture d’écran de OLE DB lien de Pages de données - onglet Connexion](../media/data-link-pages-connection-tab.png)

L’onglet Connexion est propre à chaque fournisseur et affiche uniquement les propriétés de connexion requises par Microsoft OLE DB Driver for SQL Server.

|Option|Description|
|---   |---        |
|Sélectionnez ou entrez un nom de serveur.|Sélectionnez le nom d'un serveur dans la liste déroulante ou tapez l'emplacement du serveur sur lequel se trouve la base de données à laquelle vous souhaitez accéder. La sélection de la base de données sur le serveur est une action distincte. Mettez à jour la liste en cliquant sur « Actualiser ».
|Entrez les informations pour vous connecter au serveur|Vous pouvez sélectionner les options d’authentification suivantes à partir de cette liste déroulante : <ul><li>`Windows Authentication:` Authentification sur SQL Server à l’aide des informations d’identification du compte actuellement connecté en l’utilisateur Windows.</li><li>`SQL Server Authentication:` Authentification sur SQL Server à l’aide d’un ID de connexion et mot de passe.</li><li>`Active Directory - Integrated:` Authentification intégrée à l’aide des informations d’identification du compte actuellement connecté en l’utilisateur Windows.</li><li>`Active Directory - Password:` Authentification Active Directory à l’aide d’un ID de connexion et mot de passe.</li></ul>|
|SPN du serveur|Si vous utilisez une connexion approuvée, vous pouvez spécifier un nom de principal de service (SPN) pour le serveur.|
|Nom d’utilisateur|Tapez l’ID d’utilisateur à utiliser pour l’authentification lors de la connexion à la source de données.|
|Mot de passe|Tapez le mot de passe à utiliser pour l’authentification lors de la connexion à la source de données.|
|Mot de passe vide|Lorsqu’elle est activée, permet au fournisseur spécifié à utiliser un mot de passe vide dans la chaîne de connexion.|
|Autoriser l'enregistrement du mot de passe|Lorsqu’elle est activée, permet le mot de passe sera enregistré avec la chaîne de connexion. Le fait que le mot de passe soit inclus ou non dans la chaîne de connexion dépend de la fonctionnalité de l'application appelante. <br/><br/>**REMARQUE :** s’il est enregistré, le mot de passe est retourné puis enregistré comme non masqué et non chiffré.|
|Utiliser le chiffrement renforcé pour les données|Lorsqu’elle est activée, les données qui sont transmises via la connexion seront chiffrées.|
|Faire confiance au certificat de serveur|Lorsqu’elle est activée, le certificat du serveur sera validé. Certificat de serveur doit avoir le nom d’hôte correct du serveur et émis par une autorité de certification approuvée.|
|Sélectionner la base de données|Sélectionnez ou tapez le nom de base de données que vous souhaitez accéder.|
|Joindre un fichier de base de données en tant que nom de base de données|Indique le nom du fichier primaire d'une base de données joignable. Cette base de données est jointe et utilisée comme base de données par défaut pour la source de données. Dans la première zone de texte sous cette section, tapez le nom de la base de données à utiliser pour le fichier de base de données attachée.<br/><br/>Tapez le chemin d’accès complet au fichier de base de données à attacher dans la zone de texte intitulée `Using the filename`, ou cliquez sur le `...` bouton pour rechercher le fichier de base de données.|
|Modification du mot de passe|Affiche la boîte de dialogue de mot de passe de modification SQL Server. |
|Tester la connexion|Cliquez sur pour tenter une connexion à la source de données spécifié. Si la connexion échoue, vérifiez que les paramètres sont corrects. Par exemple, les fautes d'orthographe ou de respect de la casse peuvent empêcher les connexions.|

## <a name="advanced-tab"></a>Onglet Avancé
Utilisez l’onglet Avancé pour afficher et définir les propriétés d’initialisation supplémentaires.

![Capture d’écran de OLE DB lien de Pages de données - onglet Avancé](../media/data-link-pages-advanced-tab.png)

|Option|Description|
|---   |---        |
| Connect timeout | Spécifie la quantité de temps (en secondes) que le pilote Microsoft OLE DB pour SQL Server attend la fin de l’initialisation. Si l'initialisation dépasse le délai imparti, une erreur est renvoyée et la connexion n'est pas créée.|


> [!NOTE]  
>  Pour plus d’informations de connexion de liaison de données plus générales, consultez le [Data Link API Overview](https://go.microsoft.com/fwlink/?linkid=2067432).

## <a name="next-steps"></a>Étapes suivantes
- [S’authentifier auprès d’Azure Active Directory](../features/using-azure-active-directory.md) l’utilisation du pilote OLE DB.

- [Inviter l’utilisateur à des informations d’identification de l’authentification](../help-topics/sql-server-login-dialog.md) l’utilisation du pilote OLE DB.