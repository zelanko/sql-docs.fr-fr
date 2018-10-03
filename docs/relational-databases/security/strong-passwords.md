---
title: Mots de passe forts | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server], passwords
- passwords [SQL Server], strong
- symbols [SQL Server]
- security [SQL Server], passwords
- passwords [SQL Server], symbols
- characters [SQL Server], password policies
- strong passwords [SQL Server]
ms.assetid: 338548f4-c4d8-47ca-b597-5c9c0f2fa205
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3d88513efe41a9c6b5662477d429abc5a8ce7ee4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47699419"
---
# <a name="strong-passwords"></a>Mots de passe forts
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Les mots de passe peuvent représenter le point le plus faible dans le déploiement de sécurité d'un serveur. Vous devez toujours faire preuve de la plus grande attention lorsque vous choisissez un mot de passe. Un mot de passe fort présente les caractéristiques suivantes :  
  
-   il comprend au moins 8 caractères ;  
  
-   il combine des lettres, des chiffres et des symboles ;  
  
-   il ne se trouve pas dans un dictionnaire ;  
  
-   il ne correspond pas au nom d'une commande ;  
  
-   il ne correspond pas au nom d'une personne ;  
  
-   il ne correspond pas au nom d'un utilisateur ;  
  
-   il ne correspond pas au nom d'un ordinateur ;  
  
-   il est modifié régulièrement ;  
  
-   il est complètement différent des mots de passe précédents.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Les mots de passe peuvent compter jusqu’à 128 caractères, comprenant des lettres, des symboles et des chiffres. Étant donné que les noms de connexion, les noms d'utilisateurs, les rôles et les mots de passe sont souvent utilisés dans des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] , certains symboles doivent être placés entre guillemets (") ou crochets ([ ]). Utilisez ces délimiteurs dans les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] lorsque le nom de connexion, le nom d'utilisateur, le rôle ou le mot de passe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] présente les caractéristiques suivantes :  
  
-   il contient ou commence par un espace ;  
  
-   il commence par le caractère $ ou \@.  
  
 Un nom d’accès ou un mot de passe, s’il est utilisé dans une chaîne de connexion OLE DB ou ODBC, ne doit pas contenir les caractères suivants: [] {}() , ; ? * ! \@. Ces caractères servent en effet à initialiser une connexion ou à séparer les valeurs de la chaîne de connexion.  
  
## <a name="related-content"></a>Contenu associé  
 [Stratégie de mot de passe](../../relational-databases/security/password-policy.md)  
  
  
