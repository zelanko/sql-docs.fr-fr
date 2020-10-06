---
title: Authentification dans SQL Server
description: Découvrez les connexions et l’authentification dans SQL Server lors de l’utilisation d’ADO.NET et où trouver des informations supplémentaires.
ms.date: 09/26/2019
dev_langs:
- csharp
ms.assetid: 646ddbf5-dd4e-4285-8e4a-f565f666c5cc
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 8bdcc51fad2bbc14499b60a1986bec5d2bcb6a1e
ms.sourcegitcommit: 2600a414c321cfd6dc6daf5b9bcbc9a99c049dc4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91603485"
---
# <a name="authentication-in-sql-server"></a>Authentification dans SQL Server

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

SQL Server prend en charge deux modes d’authentification : le mode d’authentification Windows et le mode mixte.  
  
- L’authentification Windows correspond au mode par défaut, et il est souvent qualifié de sécurité intégrée car ce modèle de sécurité SQL Server est étroitement intégré à Windows. Des comptes d’utilisateur et groupes Windows spécifiques sont approuvés pour se connecter à SQL Server. Les utilisateurs Windows qui ont déjà été authentifiés n’ont pas besoin de présenter des informations d’identification supplémentaires.  
  
- Le mode mixte prend en charge l’authentification par Windows et par SQL Server. Les paires nom d’utilisateur–mot de passe sont conservées dans SQL Server.  
  
> [!IMPORTANT]
> Nous vous recommandons d’utiliser l’authentification Windows dans la mesure du possible. L’authentification Windows utilise une série de messages chiffrés pour authentifier les utilisateurs dans SQL Server. Quand des connexions SQL Server sont utilisées, les noms de connexion SQL Server et les mots de passe chiffrés sont transmis sur le réseau, ce qui les rend moins sûrs.  
  
Avec l’authentification Windows, les utilisateurs ont déjà ouvert une session Windows et n’ont pas besoin d’ouvrir une session SQL Server distincte. Le `SqlConnection.ConnectionString` suivant spécifie l’authentification Windows sans que les utilisateurs aient besoin de spécifier un nom d’utilisateur ou un mot de passe.  
  
```csharp
"Server=MSSQL1;Database=AdventureWorks;Integrated Security=true;  
```  
  
> [!NOTE]
> Les connexions sont différentes des utilisateurs de base de données. Vous devez mapper des connexions ou des groupes Windows à des utilisateurs ou des rôles de base de données dans une opération distincte. Vous accordez ensuite des autorisations aux utilisateurs ou aux rôles pour accéder aux objets de base de données.  
  
## <a name="authentication-scenarios"></a>Scénarios d’authentification  
L’authentification Windows est généralement le meilleur choix dans les situations suivantes :  
  
- Il y a un contrôleur de domaine.  
  
- L’application et la base de données se trouvent sur le même ordinateur.  
  
- Vous utilisez une instance de SQL Server Express ou LocalDB.  
  
Les connexions SQL Server sont souvent utilisées dans les situations suivantes :  
  
- Si vous avez un groupe de travail.  
  
- Les utilisateurs se connectent à partir de domaines différents et non approuvés.  
  
- Applications Internet, comme ASP.NET.  
  
> [!NOTE]
> La spécification de l’authentification Windows ne désactive pas les connexions SQL Server. Utilisez l’instruction Transact-SQL ALTER LOGIN DISABLE pour désactiver des connexions SQL Server dotées de privilèges élevés.  
  
## <a name="login-types"></a>Types de connexion  
SQL Server prend en charge trois types de connexions :  
  
- Un compte d’utilisateur Windows local ou un compte de domaine approuvé. SQL Server s’appuie sur Windows pour authentifier les comptes d’utilisateur Windows.  
  
- Groupe Windows. L’octroi de l’accès à un groupe Windows accorde l’accès à toutes les connexions utilisateur Windows qui sont membres du groupe.  
  
- Connexion SQL Server. SQL Server stocke le nom d’utilisateur et un hachage du mot de passe dans la base de données MASTER, en utilisant des méthodes d’authentification internes pour vérifier les tentatives de connexion.  
  
> [!NOTE]
> SQL Server fournit des connexions créées à partir de certificats ou de clés asymétriques qui sont utilisées seulement pour la signature de code. Elles ne peuvent pas être utilisées pour se connecter à SQL Server.  
  
## <a name="mixed-mode-authentication"></a>Mode d’authentification mixte  
Si vous devez utiliser l’authentification en mode mixte, vous devez créer des connexions SQL Server, qui sont stockées dans SQL Server. Vous devez ensuite fournir le nom d’utilisateur et le mot de passe SQL Server au moment de l’exécution.  
  
> [!IMPORTANT]
> SQL Server est installé avec une connexion SQL Server nommée `sa` (abréviation d’« administrateur système »). Attribuez un mot de passe fort à la connexion `sa` et n’utilisez pas la connexion `sa` dans votre application. La connexion `sa` est mappée au rôle serveur fixe `sysadmin`, qui a des informations d’identification d’administration irrévocables sur l’ensemble du serveur. Il n’existe aucune limite aux dommages potentiels si une personne malveillante obtient l’accès en tant qu’administrateur système. Tous les membres du groupe `BUILTIN\Administrators` Windows (groupe des administrateurs locaux) sont membres du rôle `sysadmin` par défaut, mais peuvent être supprimés de ce rôle.  
  
> [!IMPORTANT]
> La concaténation de chaînes de connexion à partir d’entrées utilisateur peut vous rendre vulnérable à une attaque par injection de chaîne de connexion. Utilisez le <xref:Microsoft.Data.SqlClient.SqlConnectionStringBuilder> pour créer des chaînes de connexion syntaxiquement valides au moment de l’exécution. 
  
## <a name="external-resources"></a>Ressources externes  
Pour plus d'informations, consultez les ressources ci-dessous.  
  
|Ressource|Description|  
|--------------|-----------------|  
|[Principaux](../../../relational-databases/security/authentication-access/principals-database-engine.md)|Décrit les connexions et autres principaux de sécurité dans SQL Server.|  
  
## <a name="next-steps"></a>Étapes suivantes
- [Scénarios de sécurité des applications dans SQL Server](application-security-scenarios-sql-server.md)
