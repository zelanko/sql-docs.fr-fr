---
title: Azure Active Directory dans SQL Server Data Tools (SSDT) | Microsoft Docs
ms.custom: ''
ms.date: 10/28/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: ssdt
ms.topic: conceptual
author: stevestein
ms.author: sstein
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 302345a2d7e8c1bd9192c91c6f88253c9a4668f2
ms.sourcegitcommit: 4fb6bc7c81a692a2df706df063d36afad42816af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73049899"
---
# <a name="azure-active-directory-support-in-sql-server-data-tools-ssdt"></a>Prise en charge d’Azure Active Directory dans SQL Server Data Tools (SSDT)

[!INCLUDE[appliesto-xx-asdb-asdb-xxx-md.md](../includes/appliesto-xx-asdb-asdw-xxx-md.md)]

SQL Server Data Tools (SSDT) fournit plusieurs méthodes d’authentification [Azure Active Directory (Azure AD)](https://docs.microsoft.com/azure/active-directory/active-directory-whatis).

Dans Visual Studio, ouvrez l’**Explorateur d’objets SQL Server** (dans le menu **Afficher**), puis sélectionnez **Ajouter SQL Server** :

![Boîte de dialogue de connexion à SSDT](media/azure-active-directory/interactive.png)

#### <a name="which-azure-sql-products"></a>Quels produits SQL Azure ?

Cet article aborde Azure AD pour la liste suivante de *produits SQL Azure* dans le [cloud Azure](https://azure.microsoft.com/) :

- Azure SQL Database
- Azure SQL Data Warehouse.

## <a name="active-directory-password-authentication"></a>Authentification par mot de passe Active Directory

*L’authentification par mot de passe Active Directory* est un mécanisme de connexion aux produits SQL Azure répertoriés précédemment. Le mécanisme utilise des identités dans Azure Active Directory (Azure AD). Utilisez cette méthode de connexion dans les cas suivants :

- Vous êtes connecté à Windows avec les informations d’identification d’un domaine qui n’est pas fédéré avec Azure.
- Vous utilisez l’authentification Azure AD avec Azure AD, et elle est basée sur le domaine initial ou client.

Pour plus d’informations, voir [Connexion à la base de données SQL à l’aide de l’authentification Azure Active Directory](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication).  

## <a name="active-directory-integrated-authentication"></a>Authentification intégrée à Active Directory

*L’authentification intégrée à Active Directory* est un mécanisme de connexion aux produits SQL Azure répertoriés qui utilise des identités dans Azure Active Directory (Azure AD). Utilisez cette méthode pour vous connecter si vous êtes connecté à Windows avec vos informations d’identification Azure Active Directory à partir d’un domaine fédéré. Pour plus d’informations, voir [Connexion à la base de données SQL à l’aide de l’authentification Azure Active Directory](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication).

## <a name="active-directory-interactive-authentication"></a>Authentification interactive Active Directory

*L’authentification interactive Active Directory* est disponible lors de la connexion aux produits SQL Azure répertoriés avec SSDT, mais uniquement avec le [.NET Framework 4.7.2](https://docs.microsoft.com/dotnet/api/?view=netframework-4.7.2) ou ultérieur.

- [Téléchargez et installez le .NET Framework (n’importe quelle version)](https://www.microsoft.com/net/download/all).
- [Visual Studio 2017 15.6](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-relnotes) ou ultérieur.

#### <a name="multi-factor-authentication-mfa"></a>L’authentification multifacteur (MFA)

L’authentification interactive Active Directory prend en charge une authentification interactive qui vous permet d’utiliser Azure Active Directory (AD) Multi-Factor Authentication (MFA) pour vous authentifier auprès des produits SQL Azure répertoriés. Cette méthode prend en charge les utilisateurs Azure AD natifs et fédérés, ainsi que les utilisateurs invités d’autres comptes. Parmi les autres types de compte, citons les suivants :

- Utilisateurs entreprise-entreprise (Azure AD B2B).
- Comptes Microsoft, tels que @outlook.com, @hotmail.com et @live.com.
- Comptes non-Microsoft, tels que @gmail.com.

Si la méthode MFA est spécifiée, le **Nom d’utilisateur** doit être spécifié et le champ **Mot de passe** est désactivé. 

#### <a name="password-entry"></a>Entrée de mot de passe

Lors de l’authentification avec *l’authentification interactive Active Directory*, une fenêtre d’authentification s’ouvre qui oblige les utilisateurs à entrer un mot de passe manuellement.

![boîte de dialogue de connexion](media/azure-active-directory/sign-in.png)

La mise en œuvre de MFA est fournie par Azure AD par le biais de cette fenêtre contextuelle MFA supplémentaire.

> [!NOTE]
> Les flux de travail automatisés sont bloqués par l’utilisation de *l’authentification interactive Active Directory*. Une personne doit être disponible pour interagir avec le processus d’authentification, c’est-à-dire qu’elle doit entrer manuellement un mot de passe.

## <a name="known-issues-and-limitations"></a>Problèmes connus et limitations

- *L’authentification Interactive Active Directory* est uniquement prise en charge lors de la connexion aux produits SQL Azure répertoriés au début de cet article. Elle n’est pas prise en charge pour SQL Server (en local ou sur une machine virtuelle).
- *L’authentification interactive Active Directory* n’est pas prise en charge dans la boîte de dialogue de connexion de *l’Explorateur de serveurs*. Vous devez vous connecter à l’aide de SSDT avec *l’Explorateur d’objets SQL Server*.
- L’intégration de l’authentification unique avec le compte actuellement connecté dans Visual Studio n’est pas prise en charge pour SSDT.
- Le fichier SQLPackage.exe installé dans le répertoire Extensions durant l’installation de Visual Studio n’est pas destiné à être utilisé à partir de cet emplacement. Pour utiliser SQLpackage.exe avec Azure AD, accédez à [https://www.microsoft.com/download/details.aspx?id=55088](https://www.microsoft.com/download/details.aspx?id=55088). 
- La comparaison de données SSDT n’est pas prise en charge pour l’authentification Azure AD.  


## <a name="see-also"></a>Voir aussi  

[Authentification multifacteur](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication)  
[Authentification Azure Active Directory avec SQL Database](https://docs.microsoft.com/azure/sql-database/sql-database-aad-authentication-configure)  
[Forum MSDN SSDT](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=ssdt)  
[Blog de l’équipe SSDT](https://blogs.msdn.com/b/ssdt/)  
[Référence de l’API DACFx](https://msdn.microsoft.com/library/dn645454.aspx)  
[Télécharger SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)  
