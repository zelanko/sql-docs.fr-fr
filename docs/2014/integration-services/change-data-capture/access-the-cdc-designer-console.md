---
title: Accéder à la console CDC Designer | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- accMsDes
ms.assetid: b168c64e-c1b5-42d4-a92a-84de1dd0324e
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 58f712111dfa93bbac03bb984c30b87521b5be14
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84923927"
---
# <a name="access-the-cdc-designer-console"></a>Accéder à la console du concepteur CDC
  Vous pouvez accéder à la console du concepteur CDC à partir de l'ordinateur sur lequel vous avez installé la console. Pour plus d'informations sur l'installation, consultez Installation.  
  
 Lorsque vous ouvrez la console du concepteur CDC, la boîte de dialogue Connexion à SQL Server s'ouvre.  
  
 La connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui accède au concepteur CDC doit avoir les autorisations UPDATE sur la base de données MSXDBCDC. En outre, la connexion doit également disposer du rôle serveur fixe `dbcreator` pour créer des instances Oracle CDC. Il est recommandé que la connexion ait également un accès SELECT aux bases de données CDC qui sont utilisées, sinon l'utilisateur ne peut pas afficher l'état de ces bases de données.  
  
 Dans la boîte de dialogue Connexion à SQL Server, entrez les informations suivantes :  
  
### <a name="server-name"></a>Nom du serveur  
 Tapez le nom du serveur où se trouve [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="authentication"></a>Authentification  
 Sélectionnez l’un des suivants :  
  
-   **Authentification Windows**  
  
-   **Authentification SQL Server** : si vous sélectionnez cette option, vous devez taper **l’Identifiant** et le **Mot de passe** de l’utilisateur dans l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à laquelle vous vous connectez.  
  
 La connexion doit avoir un rôle de base de données qui permet l'accès à la base de données MSXCDCDB. Il est recommandé que la connexion ait également accès à toutes les bases de données supplémentaires qui sont utilisées, sinon l'utilisateur ne pourra pas afficher les données de ces bases de données.  
  
### <a name="options"></a>Options  
 Cliquez sur la flèche pour afficher les options disponibles à configurer. Vous pouvez choisir de conserver ces options avec leur valeur par défaut. Options disponibles :  
  
 **Délai de connexion**  
 Tapez le délai (en secondes) pendant lequel le service de capture de données modifiées pour Oracle attend une connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avant expiration. La valeur par défaut est **15**.  
  
 **Délai d'exécution**  
 Tapez le délai (en secondes) pendant lequel le service Windows de capture de données modifiées Oracle attend l'exécution d'une commande avant expiration. La valeur par défaut est **30**.  
  
 **Chiffrer la connexion**  
 Sélectionnez **Chiffrer la connexion** pour utiliser une connexion chiffrée dans la communication entre Oracle CDC Service et l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cible.
**Avancé** : Cliquez sur **Avancé** et tapez toutes les propriétés de connexion supplémentaires dans la boîte de dialogue Propriétés avancées de connexion, si nécessaire.  
  
 **Avancée**  
 Cliquez sur **Avancé** et tapez toutes les propriétés de connexion supplémentaires dans la boîte de dialogue Propriétés avancées de connexion, si nécessaire.  
  
 Pour plus d’informations sur la boîte de dialogue Propriétés avancées de connexion, consultez [Propriétés avancées de connexion](advanced-connection-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Autorisations de connexion SQL Server nécessaires pour le concepteur CDC](sql-server-connection-required-permissions-for-the-cdc-designer.md)  
  
  
