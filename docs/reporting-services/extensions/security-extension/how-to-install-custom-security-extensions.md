---
title: "Comment installer les extensions de sécurité personnalisées | Documents Microsoft"
ms.custom: 
ms.date: 07/10/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bfa0a35b-ccfb-4279-bae6-106c227c5f16
caps.latest.revision: 3
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 47182ebd082dfae0963d761e54c4045be927d627
ms.openlocfilehash: 58cfeef7d74e0641b965c307551f0fba4a7ff09c
ms.contentlocale: fr-fr
ms.lasthandoff: 08/09/2017

---

# <a name="how-to-install-custom-security-extensions"></a>Comment installer les extensions de sécurité personnalisées

[!INCLUDE[ssrs-appliesto](../../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../../includes/ssrs-appliesto-pbirs.md)]

Reporting Services 2016 introduit un nouveau portail web pour héberger le nouveau APIs Odata et également héberger les charges de travail de nouveaux rapports tels que les rapports mobiles et indicateurs de performance clés. Ce nouveau portail s’appuie sur des technologies plus récentes et est isolé à partir de la ReportingServicesService familier par en cours d’exécution dans un processus séparé. Ce processus n’est pas une application ASP.NET hébergée et par conséquent s’arrête hypothèses à partir des extensions de sécurité personnalisé existant. En outre, ne pas autoriser les interfaces actuels pour les extensions de sécurité personnalisées pour n’importe quel contexte externe soit passée, en laissant l’attention des implémenteurs avec le seul choix possible d’inspecter des objets ASP.NET global bien connue, cela nécessaire certaines modifications apportées à l’interface.

## <a name="what-changed"></a>Ce qui a été changé

A été introduite une nouvelle interface qui peut être implémentée qui fournit un IRSRequestContext qui fournit les propriétés plus communes utilisées par les extensions pour prendre des décisions relatives à l’authentification.

Dans les versions précédentes, le Gestionnaire de rapports a été le serveur frontal et peut être configuré avec sa propre page de connexion personnalisée. Dans Reporting Services 2016, qu’une seule page hébergée par reportserver est pris en charge et doit-elle s’authentifier pour les deux applications.

## <a name="implementation"></a>Implémentation

Dans les versions précédentes, les extensions pouvaient se fier à une hypothèse courantes que les objets ASP.NET serait rapidement disponibles. Étant donné que le nouveau portail ne fonctionne pas dans ASP.NET, l’extension peut-être atteints problèmes avec les objets de valeur null.

L’exemple plus générique accède à HttpContext.Current pour lire les informations de requête tels que les en-têtes et les cookies. Pour autoriser les extensions de prendre les décisions de mêmes, nous avons introduit une nouvelle méthode dans l’extension qui fournit des informations de requête et est appelée lors de l’authentification à partir du portail. 

Extensions doivent implémenter le <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension2> interface afin de tirer parti de cela. Les extensions devez implémenter les deux versions de <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension.GetUserInfo%2A> méthode est appelée par le reportserver contexte et les autres utilisé dans le processus de l’hôte Web. L’exemple ci-dessous montre une des implémentations simples pour le portail où l’identité résolue reportserver est celui utilisé.

``` 
public void GetUserInfo(IRSRequestContext requestContext, out IIdentity userIdentity, out IntPtr userId)
{
    userIdentity = null;
    if (requestContext.User != null)
    {
        userIdentity = requestContext.User;
    }

    // initialize a pointer to the current user id to zero
    userId = IntPtr.Zero;
}
```

## <a name="deployment-and-configuration"></a>Déploiement et Configuration

Les configurations de base nécessaires pour l’extension de sécurité personnalisée sont les mêmes que les versions précédentes. Modifications sont nécessaires pour le fichier web.config et rsreportserver.config : pour plus d’informations, consultez [personnalisé de configurer ou de l’authentification par formulaire sur le serveur de rapports](../../../reporting-services/security/configure-custom-or-forms-authentication-on-the-report-server.md).

Il n’est plus un web.config distincte pour le Gestionnaire de rapports, le portail héritera les mêmes paramètres que le point de terminaison reportserver.

## <a name="machine-keys"></a>Clés d’ordinateur

Dans le cas de l’authentification par formulaire, ce qui nécessite le déchiffrement du cookie d’authentification, les deux processus doivent être configurés avec l’algorithme de clé et le déchiffrement même ordinateur. Il s’agissait d’une étape familier pour ceux qui était auparavant le programme d’installation Reporting Services pour travailler sur des environnements de montée en puissance parallèle, mais maintenant est requis même pour les déploiements sur un seul ordinateur.

Vous devez utiliser une clé spécifique à validation pour le déploiement vous, il existe plusieurs outils pour générer les clés telles que les Services Gestionnaire (IIS). Autres outils sont accessibles sur internet.

### <a name="sql-server-reporting-services-2017-and-later"></a>SQL Server Reporting Services 2017 et versions ultérieures

**\ReportServer\rsReportServer.config**

Ajouter sous `<configuration>`.

```
<machineKey validationKey="[YOUR KEY]" decryptionKey=="[YOUR KEY]" validation="AES" decryption="AES" />
```

### <a name="sql-server-reporting-services-2016"></a>SQL Server Reporting Services 2016

**\ReportServer\web.config**

Ajouter sous `<system.web>`.
    
```
    <machineKey validationKey="[YOUR KEY]" decryptionKey=="[YOUR KEY]" validation="AES" decryption="AES" />
```

**\RSWebApp\Microsoft.ReportingServices.Portal.WebHost.exe.config**

Ajouter sous `<configuration>`.

```
    <system.web>
        <machineKey validationKey=="[YOUR KEY]" decryptionKey=="[YOUR KEY]" validation="AES" decryption="AES" />
    </system.web>
```

### <a name="power-bi-report-server"></a>Power BI Report Server

Il est disponible à partir de la version de juin 2017 (Build 14.0.600.301).

**\ReportServer\rsReportServer.config**

Ajouter sous `<configuration>`.

```
<machineKey validationKey="[YOUR KEY]" decryptionKey=="[YOUR KEY]" validation="AES" decryption="AES" />
```

## <a name="configure-passthrough-cookies"></a>Configurer les cookies de relais

Le nouveau portail et reportserver communiquent à l’aide de soap interne API pour certaines de ses opérations (semblables à la version précédente du Gestionnaire de rapports). Lorsque des cookies supplémentaires sont requis pour être transmis à partir du portail sur le serveur, les propriétés PassThroughCookies est toujours disponible. Pour plus d’informations, consultez [configurer le portail Web pour passer des Cookies d’authentification personnalisée](../../../reporting-services/security/configure-the-web-portal-to-pass-custom-authentication-cookies.md).

```
<UI>
   <CustomAuthenticationUI>
      <PassThroughCookies>
         <PassThroughCookie>sqlAuthCookie</PassThroughCookie>
      </PassThroughCookies>
   </CustomAuthenticationUI>
</UI>
```

## <a name="next-steps"></a>Étapes suivantes

[Configurer l’authentification par formulaires ou personnalisée sur le serveur de rapports](../../../reporting-services/security/configure-custom-or-forms-authentication-on-the-report-server.md)  
[Configurer le Gestionnaire de rapports pour transmettre des Cookies d’authentification personnalisée](https://msdn.microsoft.com/library/ms345241(v=sql.120).aspx)

D’autres questions ? [Essayez de poser le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)
