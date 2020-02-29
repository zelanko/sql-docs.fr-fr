---
title: Autorisation dans Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- authorization [Reporting Services]
ms.assetid: 15fc1c7b-560c-4737-b126-e0d428a1b530
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 79c0e947ce20c8c8393e4a87cf7f2f9f86203d39
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78176989"
---
# <a name="authorization-in-reporting-services"></a>Autorisation dans Reporting Services
  L'autorisation est le processus permettant de déterminer si une identité peut se voir accorder le type d'accès demandé à une ressource donnée dans la base de données du serveur de rapports. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] utilise une architecture d'autorisation basée sur les rôles qui permet à un utilisateur d'accéder à une ressource donnée en fonction de l'attribution de rôle de l'utilisateur pour l'application. Les extensions de sécurité pour [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] contiennent une implémentation d'un composant d'autorisation servant à accorder l'accès aux utilisateurs une fois ceux-ci authentifiés sur le serveur de rapports. L'autorisation est appelée lorsqu'un utilisateur tente d'effectuer une opération sur le système ou sur un élément du serveur de rapports par le biais de l'API SOAP et via l'accès URL. Cela est possible grâce à l'interface d'extension de sécurité **IAuthorizationExtension**. Comme indiqué précédemment, toutes les extensions héritent d' **IExtension** , l'interface de base pour n'importe quelle extension que vous déployez. **IExtension** et **IAuthorizationExtension** sont membres de l’espace de noms **Microsoft. ReportingServices. interfaces** .

## <a name="checking-access"></a>Vérification de l'accès
 En matière d'autorisation, l'élément fondamental de toute implémentation de sécurité personnalisée est la vérification de l'accès, qui est implémentée dans la méthode <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A>. <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> est appelé chaque fois qu'un utilisateur tente une opération sur le serveur de rapports. La méthode <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> est surchargée pour chaque type d'opération. Voici un exemple de vérification d'accès pour les opérations de dossier :

```
// Overload for Folder operations
public bool CheckAccess(
   string userName, 
   IntPtr userToken, 
   byte[] secDesc, 
   FolderOperation requiredOperation)
{
   // If the user is the administrator, allow unrestricted access.
   if (userName == m_adminUserName) 
      return true;

   AceCollection acl = DeserializeAcl(secDesc);
   foreach(AceStruct ace in acl)
   {
         if (userName == ace.PrincipalName)
         {
            foreach(FolderOperation aclOperation in 
               ace.FolderOperations)
            {
               if (aclOperation == requiredOperation)
                     return true;
            }
         }
   }
   return false;
}
```

 Le serveur de rapports appelle la méthode <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> en passant le nom de l'utilisateur connecté, un jeton utilisateur, le descripteur de sécurité de l'élément et l'opération demandée dans le nom de l'utilisateur connecté. Ici, vous devez vérifier le descripteur de sécurité pour le nom d'utilisateur et l'autorisation appropriée pour effectuer la demande, puis retourner `true` pour indiquer que l'accès est accordé ou `false` pour indiquer que l'accès est refusé.

## <a name="security-descriptors"></a>Descripteurs de sécurité
 Lors de la définition de stratégies d'autorisation sur des éléments dans la base de données du serveur de rapports, une application cliente (telle que le Gestionnaire de rapports) envoie les informations utilisateur ainsi qu'une stratégie de sécurité pour l'élément à l'extension de sécurité. La stratégie de sécurité et les informations utilisateur sont désignées collectivement sous le nom de « descripteur de sécurité ». Un descripteur de sécurité contient les informations suivantes pour un élément dans la base de données du serveur de rapports :

-   le groupe ou l'utilisateur étant autorisé d'une certaine manière à effectuer des opérations sur l'élément ;

-   le type de l'élément ;

-   une liste de contrôle d'accès discrétionnaire qui contrôle l'accès à l'élément.

 Les descripteurs de sécurité sont créés à l'aide des méthodes <xref:ReportService2010.ReportingService2010.SetPolicies%2A> et <xref:ReportService2010.ReportingService2010.SetSystemPolicies%2A> du service Web.

### <a name="authorization-flow"></a>Flux d'autorisation
 L'autorisation [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] est contrôlée par l'extension de sécurité actuellement configurée pour s'exécuter sur le serveur. L'autorisation, basée sur les rôles, est limitée aux autorisations et aux opérations fournies par l'architecture de la sécurité [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] . Le diagramme suivant représente le processus permettant d'autoriser des utilisateurs à manipuler des éléments dans la base de données du serveur de rapports :

 ![Flux d'autorisation de sécurité de Reporting Services](../../media/rosettasecurityextensionauthorizationflow.gif "Flux d'autorisation de sécurité de Reporting Services")

 Comme représenté dans ce diagramme, l'autorisation suit la séquence suivante :

1.  Une fois authentifié, les applications clientes font des demandes au serveur de rapports par le biais des méthodes du service Web Reporting Services. Un ticket d'authentification est passé au serveur de rapports sous forme d'un cookie dans l'en-tête HTTP de chaque demande Web.

2.  Le cookie est validé avant toute vérification d'accès.

3.  Une fois le cookie validé, le serveur de rapports appelle <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension.GetUserInfo%2A> et une identité est attribuée à l'utilisateur.

4.  L'utilisateur tente une opération par le biais du service Web Reporting Services.

5.  Le serveur de rapports appelle la méthode <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A>.

6.  Le descripteur de sécurité est récupéré et passé à une implémentation d'extension de sécurité personnalisée de <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A>. À ce stade, l'utilisateur, le groupe ou l'ordinateur est comparé au descripteur de sécurité de l'élément en cours d'accès et est autorisé à effectuer l'opération demandée.

7.  Si l'utilisateur est autorisé, le service Web effectue l'opération et retourne une réponse à l'application appelante.


