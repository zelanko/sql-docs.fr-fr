---
title: Boîte de dialogue de connexion SQL Server (OLE DB) | Microsoft Docs
description: Utilisation de la boîte de dialogue de connexion SQL Server
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
ms.author: v-beaziz
author: bazizi
ms.openlocfilehash: 4735ead33dc7c3a6d633e3b23ff1da97eeae4962
ms.sourcegitcommit: 958cffe9288cfe281280544b763c542ca4025684
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56744831"
---
# <a name="sql-server-login-dialog-box"></a>Boîte de dialogue de connexion SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Lorsque vous tentez de vous connecter sans spécifier suffisamment d’informations, le pilote OLE DB affiche le **connexion à SQL Server** boîte de dialogue.

> [!NOTE]  
> Boîte de dialogue Connexion de serveur SQL le comportement d’invite est contrôlé par le `DBPROP_INIT_PROMPT` propriété d’initialisation. Pour plus d'informations, consultez :
> - [Propriétés d’initialisation et d’autorisation](../ole-db-data-source-objects/initialization-and-authorization-properties.md)
> - [Guide du programmeur OLE DB](https://go.microsoft.com/fwlink/?linkid=2067702)

![Capture d’écran de la boîte de dialogue de connexion SQL Server](../media/sql-server-login-dialog.png)

## <a name="options"></a>Options
|Option|Description|
|---   |---        |
|Serveur|Le nom d’une instance de SQL Server sur votre réseau. Tapez le nom serveur\instance dans la zone **Serveur**, ou sélectionnez-en un dans la liste. Vous pouvez si vous le souhaitez créer un alias de serveur sur l’ordinateur client avec le **Gestionnaire de configuration SQL Server** et taper ce nom dans la zone **Serveur**. <br/><br/>Vous pouvez entrer "(local)" lorsque vous utilisez le même ordinateur que SQL Server. Vous pouvez alors vous connecter à une instance locale de SQL Server, même s’il s’agit d’une version de SQL Server qui n’est pas en réseau.<br/><br/>Pour plus d’informations sur les noms de serveur pour différents types de réseaux, consultez [Installation de SQL Server](https://go.microsoft.com/fwlink/?linkid=2067541).|
|Mode d'authentification|Vous pouvez sélectionner les options d’authentification suivantes à partir de la liste déroulante :<br/><ul><li>`Windows Authentication:` Authentification sur SQL Server à l’aide des informations d’identification du compte actuellement connecté en l’utilisateur Windows.</li><li>`SQL Server Authentication:` Authentification sur SQL Server à l’aide d’un ID de connexion et mot de passe.</li><li>`Active Directory - Integrated:` Authentification intégrée à l’aide des informations d’identification du compte actuellement connecté en l’utilisateur Windows.</li><li>`Active Directory - Password:` Authentification Active Directory à l’aide d’un ID de connexion et mot de passe.</li></ul>|
|SPN du serveur|Si vous utilisez une connexion approuvée, vous pouvez spécifier un nom de principal de service (SPN) pour le serveur.|
|Nom d'accès|Spécifie l’ID de connexion à utiliser pour la connexion. La zone de texte d’un ID de connexion est activée uniquement si `Authentication Mode` a la valeur `SQL Server Authentication` ou `Active Directory - Password`.|
|Mot de passe|Spécifie le mot de passe utilisé pour la connexion. La zone de texte mot de passe est activée uniquement si `Authentication Mode` a la valeur `SQL Server Authentication` ou `Active Directory - Password`.|
|Options|Affiche ou masque le groupe **Options**. Le bouton **Options** est activé si **Serveur** a une valeur.|
|Modification du mot de passe|Lorsqu’elle est activée, permet **nouveau mot de passe** et **confirmer le nouveau mot de passe** zones de texte.|
|Nouveau mot de passe|Spécifie le nouveau mot de passe.|
|Confirmer le nouveau mot de passe|Spécifie une deuxième fois le nouveau mot de passe, à des fins de confirmation.|
|Base de données|Sélectionnez ou entrez la base de données par défaut à utiliser sur la connexion. Ce paramètre remplace la base de données par défaut spécifiée pour le nom de connexion sur le serveur. Si aucune base de données n'est spécifiée, la connexion utilise la base de données par défaut spécifiée pour le nom de connexion sur le serveur.|
|Serveur miroir|Indique le nom du partenaire de basculement de la base de données à mettre en miroir.|
|SPN miroir|Facultativement, vous pouvez spécifier un SPN pour le serveur miroir. Le SPN du serveur miroir est utilisé pour l'authentification mutuelle entre client et serveur.|
|Langue|Spécifie la langue nationale à utiliser pour les messages système SQL Server. La langue en question doit être installée sur l’ordinateur qui exécute SQL Server. Ce paramètre remplace la langue par défaut spécifiée pour le nom de connexion sur le serveur. Si aucune langue n'est spécifiée, la connexion utilise la langue par défaut spécifiée pour le nom de connexion sur le serveur.|
|Application Name|Spécifie le nom de l’application à stocker dans la colonne **program_name** dans la ligne de cette connexion dans **sys.sysprocesses**.|
|ID Station de travail|Spécifie l’ID de station de travail à stocker dans la colonne **hostname** dans la ligne de cette connexion dans **sys.sysprocesses**.|
|Utiliser le chiffrement renforcé pour les données|Lorsqu’elle est activée, les données qui sont transmises via la connexion seront chiffrées.|
|Faire confiance au certificat de serveur|Lorsqu’elle est activée, le certificat du serveur sera validé. Certificat de serveur doit avoir le nom d’hôte correct du serveur et émis par une autorité de certification approuvée.|

> [!NOTE]  
> Lorsque vous utilisez `Windows Authentication` ou `SQL Server Authentication` modes, **certificat de serveur de confiance** est considéré comme uniquement lorsque le **utiliser un chiffrement renforcé pour les données** est activée.

## <a name="next-steps"></a>Étapes suivantes
- [S’authentifier auprès d’Azure Active Directory](../features/using-azure-active-directory.md) l’utilisation du pilote OLE DB.
- À l’aide des informations de connexion ensemble [lien UDL (Universal Data)](data-link-pages.md).