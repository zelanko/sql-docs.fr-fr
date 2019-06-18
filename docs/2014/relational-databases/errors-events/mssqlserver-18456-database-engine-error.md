---
title: MSSQLSERVER_18456 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 18456 (Database Engine error)
ms.assetid: c417631d-be1f-42e0-8844-9f92c77e11f7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f37f2ce9ec367d136eb853ce3bffe81f22b2dc4e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62869594"
---
# <a name="mssqlserver18456"></a>MSSQLSERVER_18456
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|18456|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|LOGON_FAILED|  
|Texte du message|Échec de la connexion pour l’utilisateur '%.*ls'.%.\*ls|  
  
## <a name="explanation"></a>Explication  
 Lorsqu’une tentative de connexion est refusée en raison d’un échec d’authentification qui implique un mot de passe incorrect ou le nom d’utilisateur, un message semblable au suivant est retourné au client :  Échec de la connexion pour l'utilisateur '<nom_utilisateur>'. (Microsoft SQL Server, erreur : 18456)".  
  
 Le client reçoit également les informations supplémentaires suivantes :  
  
 Échec de la connexion pour l'utilisateur '<nom_utilisateur>'. (.Net SqlClient Data Provider) »  
  
 -----------------------------\-  
  
 « Nom du serveur : <nom_ordinateur> »  
  
 « Numéro d’erreur : 18456"  
  
 « Gravité : 14"  
  
 « État : 1"  
  
 « Numéro de ligne : 65536"  
  
 Le message suivant peut également être retourné :  
  
 « Message 18456, niveau 14, état 1, serveur <nom_ordinateur>, ligne 1 »  
  
 « Échec de la connexion pour l'utilisateur '<nom_utilisateur>'. »  
  
## <a name="additional-error-information"></a>Informations supplémentaires sur l'erreur  
 Pour des raisons de sécurité, le message d'erreur retourné au client masque délibérément la nature de l'erreur d'authentification. Toutefois, dans le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], une erreur correspondante contient un état d'erreur mappé à une condition d'échec d'authentification. Comparez l'état d'erreur à la liste suivante afin de déterminer la raison de l'échec de connexion.  
  
|État|Description|  
|-----------|-----------------|  
|1|Aucune information sur l'erreur n'est disponible. Cet état signifie généralement que vous n'avez pas l'autorisation de recevoir les informations d'erreur. Contactez votre administrateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour plus d'informations.|  
|2|ID utilisateur non valide.|  
|5|ID utilisateur non valide.|  
|6|Tentative d'utilisation d'un nom de connexion Windows avec l'authentification SQL Server.|  
|7|La connexion est désactivée et le mot de passe est incorrect.|  
|8|Le mot de passe est incorrect.|  
|9|Mot de passe non valide.|  
|11|La connexion est valide mais l'accès au serveur a échoué. Cette erreur peut se produire lorsque l'utilisateur Windows a accès à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en tant que membre du groupe des administrateurs locaux, mais que Windows ne fournit pas d'informations d'identification d'administrateur. Pour vous connecter, démarrez le programme de connexion à l’aide de l’option **Exécuter en tant qu’administrateur**, puis ajoutez l’utilisateur Windows à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en tant que connexion spécifique.|  
|12|La connexion est valide mais l'accès au serveur a échoué.|  
|18|Le mot de passe doit être modifié.|  
  
 Il existe d'autres états d'erreurs qui signifient une erreur de traitement interne inattendue.  
  
 **Une autre cause inhabituelle possible**  
  
 Motif de l'erreur **Échec d'une tentative de connexion à l'aide de l'authentification SQL Server. Le serveur est configuré pour l’authentification Windows uniquement.** Ce message peut être retourné dans les situations suivantes.  
  
-   Lorsque le serveur est configuré pour une authentification en mode mixte et qu'une connexion ODBC utilise le protocole TCP, la connexion ne spécifie pas de manière explicite que la connexion doit utiliser une connexion approuvée.  
  
-   Lorsque le serveur est configuré pour l'authentification en mode mixte et qu'une connexion ODBC utilise des canaux nommés, les informations d'identification utilisées par le client pour ouvrir le canal nommé servent à emprunter automatiquement l'identité de l'utilisateur et la connexion ne spécifie pas de manière explicite que la connexion doit utiliser une connexion approuvée.  
  
 Pour résoudre ce problème, incluez `TRUSTED_CONNECTION = TRUE` dans la chaîne de connexion.  
  
## <a name="examples"></a>Exemples  
 Dans cet exemple, l'état d'erreur d'authentification est 8. Cela indique que le mot de passe est incorrect.  
  
|Date|`Source`|Message|  
|----------|------------|-------------|  
|2007-12-05 20:12:56.34|Connexion|Erreur : 18456, gravité : 14, état : 8.|  
|2007-12-05 20:12:56.34|Connexion|Échec de la connexion pour l'utilisateur '<nom_utilisateur>'. [CLIENT : \<adresse ip >]|  
  
> [!NOTE]  
>  Quand [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installé avec le mode d’authentification Windows et modifié ultérieurement pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec le mode d’authentification Windows, la connexion **sa** est initialement désactivée. Ceci provoque l’erreur d’état 7 : « Échec de la connexion pour l’utilisateur 'sa'. » Pour activer la connexion **sa**, consultez [Modifier le mode d’authentification du serveur](../../database-engine/configure-windows/change-server-authentication-mode.md).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Si vous essayez de vous connecter à l'aide de l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vérifiez que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré en mode Authentification mixte.  
  
 Si vous essayez de vous connecter à l'aide de l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vérifiez que la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] existe et que vous l'avez orthographiée correctement.  
  
 Si vous essayez de vous connecter à l'aide de l'authentification Windows, vérifiez que vous êtes correctement connecté au domaine approprié.  
  
 Si votre erreur indique l'état 1, contactez votre administrateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Si vous essayez de vous connecter avec vos informations d’identification d’administrateur, démarrez votre application à l’aide de l’option **Exécuter en tant qu’administrateur**. Une fois connecté, ajoutez votre utilisateur Windows en tant que connexion individuelle.  
  
 Si le [!INCLUDE[ssDE](../../includes/ssde-md.md)] prend en charge les bases de données autonomes, vérifiez que la connexion n’a pas été supprimée suite à la migration vers un utilisateur de base de données autonome.  
  
 Lors de la connexion locale à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les connexions d’autres services qui s’exécutent également sous **NT AUTHORITY\NETWORK SERVICE** doivent s’authentifier à l’aide du nom de domaine complet des ordinateurs. Pour plus d’informations, consultez [Guide pratique pour Utiliser le compte de Service réseau pour accéder aux ressources dans ASP.NET](https://msdn.microsoft.com/library/ff647402.aspx)  
  
  
