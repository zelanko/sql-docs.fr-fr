---
title: Se connecter à DB2 (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 9d485fd0-ab5d-402a-a59a-e9982a61b7de
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 2a14b3a5de4292b01fd6fdb2df67bd4839d1a8d9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68141090"
---
# <a name="connect-to-db2-db2tosql"></a>Se connecter à DB2 (DB2ToSQL)
Utilisez le **se connecter à DB2** boîte de dialogue pour vous connecter à la base de données DB2 que vous souhaitez migrer.  
  
Pour accéder à cette boîte de dialogue, dans le **fichier** menu, sélectionnez **se connecter à DB2**. Si vous êtes déjà connecté, la commande est **reconnexion à DB2**.  
  
## <a name="options"></a>Options  
**Fournisseur**  
Sélectionnez le fournisseur d’accès aux données pour votre connexion à la base de données DB2. Les fournisseurs disponibles sont le fournisseur de Client DB2 et le fournisseur OLE DB. La valeur par défaut est le fournisseur de Client DB2.  
  
**Mode**  
Sélectionnez le mode Standard, TNSNAME ou chaîne de connexion.  
  
-   En mode Standard, vous entrez ou sélectionnez des valeurs pour le fournisseur, nom du serveur, port du serveur, DB2 SID, nom d’utilisateur et mot de passe.  
  
-   En mode TNSNAME, vous entrez l’identificateur de connexion (alias TNS) de la base de données DB2, le nom d’utilisateur et le mot de passe.  
  
-   En mode de chaîne de connexion, vous fournissez une chaîne de connexion.  
  
    > [!IMPORTANT]  
    > Nous vous déconseillons d’utiliser le mode de chaîne de connexion, car le texte peut inclure des mots de passe, et il est envoyé en texte clair.  
  
La valeur par défaut est en mode Standard.  
  
**Nom du serveur**  
Entrez le nom du serveur DB2. Le nom du serveur par défaut est le même que le nom de l’ordinateur. Il s’agit d’une option de mode Standard.  
  
**Port du serveur**  
Si vous utilisez un numéro de port autre que 1521 (valeur par défaut) pour les connexions à DB2, entrez le numéro de port. Il s’agit d’une option de mode Standard.  
  
**Identificateur de connexion**  
Entrez le DB2 identificateur de connexion. Il s’agit de l’alias de la base de données tel que défini dans le fichier tnsnames.ora local.  
  
Il s’agit d’une option de mode TNSNAME.  
  
**DB2 SID**  
Entrez le SID de la base de données. Le SID est un identificateur qui le distingue de la base de données DB2 sur un ordinateur. La valeur par défaut de SID pour une base de données est les huit premiers caractères du nom de base de données.  
  
Il s’agit d’une option de mode Standard.  
  
**Nom d'utilisateur**  
Entrez le nom d’utilisateur SSMA utilisera pour se connecter à la base de données DB2.  
  
**Mot de passe**  
Entrez le mot de passe correspondant au nom d'utilisateur indiqué.  
  
**Chaîne de connexion**  
> [!IMPORTANT]  
> Nous vous déconseillons d’utiliser le mode de chaîne de connexion, car le texte peut inclure des mots de passe, et il est envoyé en texte clair.  
  
Si vous utilisez le mode de chaîne de connexion, entrez la chaîne de connexion complète pour la connexion à DB2.  
  
Chaînes de connexion sont constitués de paires nom / valeur de paramètre.  
  
-   Pour plus d’informations de chaîne de connexion OLE DB, consultez [fournisseur Microsoft OLE DB pour DB2](https://go.microsoft.com/fwlink/?LinkId=85640) article dans la bibliothèque MSDN.  
  
Pour les chaînes de connexion de SSMA, toujours inclure le paramètre de fournisseur. En outre, assurez-vous que vous incluez le paramètre de Port lorsque vous vous connectez à DB2.  
  
