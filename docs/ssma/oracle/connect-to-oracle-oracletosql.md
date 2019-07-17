---
title: Se connecter à Oracle (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 23a48cb6-ff30-49bb-b4a7-603ebcab336f
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 42ab1e77dbdb7cee237a9ec22c49a725a64390c0
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68264482"
---
# <a name="connect-to-oracle-oracletosql"></a>Se connecter à Oracle (OracleToSQL)
Utilisez le **se connecter à Oracle** boîte de dialogue pour vous connecter à la base de données Oracle que vous souhaitez migrer.  
  
Pour accéder à cette boîte de dialogue, dans le **fichier** menu, sélectionnez **se connecter à Oracle**. Si vous êtes déjà connecté, la commande est **reconnexion à Oracle**.  
  
## <a name="options"></a>Options  
**Fournisseur**  
Sélectionnez le fournisseur d’accès aux données pour votre connexion à la base de données Oracle. Les fournisseurs disponibles sont le fournisseur de Client Oracle et le fournisseur OLE DB. La valeur par défaut est le fournisseur du Client Oracle.  
  
**Mode**  
Sélectionnez le mode Standard, TNSNAME ou chaîne de connexion.  
  
-   En mode Standard, vous entrez ou sélectionnez des valeurs pour le fournisseur, nom du serveur, port du serveur, Oracle SID, nom d’utilisateur et mot de passe.  
  
-   En mode TNSNAME, vous entrez l’identificateur de connexion (alias TNS) de la base de données Oracle, le nom d’utilisateur et le mot de passe.  
  
-   En mode de chaîne de connexion, vous fournissez une chaîne de connexion.  
  
    > [!IMPORTANT]  
    > Nous vous déconseillons d’utiliser le mode de chaîne de connexion, car le texte peut inclure des mots de passe, et il est envoyé en texte clair.  
  
La valeur par défaut est en mode Standard.  
  
**Nom du serveur**  
Entrez le nom du serveur Oracle. Le nom du serveur par défaut est le même que le nom de l’ordinateur. Il s’agit d’une option de mode Standard.  
  
**Port du serveur**  
Si vous utilisez un numéro de port autre que 1521 (valeur par défaut) pour les connexions à Oracle, entrez le numéro de port. Il s’agit d’une option de mode Standard.  
  
**Identificateur de connexion**  
Entrez l’Oracle de connecter l’identificateur. Il s’agit de l’alias de la base de données tel que défini dans le fichier tnsnames.ora local.  
  
Il s’agit d’une option de mode TNSNAME.  
  
**SID Oracle**  
Entrez le SID de la base de données. Le SID est un identificateur qui le distingue de la base de données Oracle sur un ordinateur. La valeur par défaut de SID pour une base de données est les huit premiers caractères du nom de base de données.  
  
Il s’agit d’une option de mode Standard.  
  
**Nom d'utilisateur**  
Entrez le nom d’utilisateur SSMA utilisera pour se connecter à la base de données Oracle.  
  
**Mot de passe**  
Entrez le mot de passe correspondant au nom d'utilisateur indiqué.  
  
**Chaîne de connexion**  
> [!IMPORTANT]  
> Nous vous déconseillons d’utiliser le mode de chaîne de connexion, car le texte peut inclure des mots de passe, et il est envoyé en texte clair.  
  
Si vous utilisez le mode de chaîne de connexion, entrez la chaîne de connexion complète pour la connexion à Oracle.  
  
Chaînes de connexion sont constitués de paires nom / valeur de paramètre.  
  
-   Pour plus d’informations de chaîne de connexion OLE DB, consultez [fournisseur Microsoft OLE DB pour Oracle](https://go.microsoft.com/fwlink/?LinkId=85640) article dans la bibliothèque MSDN.  
  
Pour les chaînes de connexion de SSMA, toujours inclure le paramètre de fournisseur. En outre, assurez-vous que vous incluez le paramètre de Port lorsque vous vous connectez à Oracle.  
  
