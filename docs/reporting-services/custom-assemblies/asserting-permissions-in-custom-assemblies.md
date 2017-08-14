---
title: "Déclaration des autorisations dans les assemblys personnalisés | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- secure calls [Reporting Services]
- custom assemblies [Reporting Services], permissions
- permission sets [Reporting Services]
- asserting permissions
- permissions [Reporting Services], custom assemblies
- limited permission sets
- security configuration files [Reporting Services]
ms.assetid: 3afb9631-f15e-405e-990b-ee102828f298
caps.latest.revision: 34
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: e98c186e950b5f4186aea4057fb63c0f27eaf1b3
ms.contentlocale: fr-fr
ms.lasthandoff: 08/12/2017

---
# <a name="asserting-permissions-in-custom-assemblies"></a>Déclaration d'autorisations dans les assemblys personnalisés
  Par défaut, code d’assembly personnalisé s’exécute avec la restriction **exécution** jeu d’autorisations. Dans certaines situations, vous voudrez peut-être implémenter un assembly personnalisé qui effectue des appels sécurisés à des ressources protégées au sein de votre système de sécurité (comme un fichier ou le Registre). Pour ce faire, vous devez procéder comme suit :  
  
1.  Identifiez les autorisations exactes dont votre code a besoin pour effectuer l'appel sécurisé. Si cette méthode fait partie d’un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] bibliothèque, ces informations doivent être incluses dans la documentation de la méthode.  
  
2.  Modifiez les fichiers de configuration de stratégie du serveur de rapports de manière à accorder les autorisations requises à l'assembly personnalisé. Pour plus d’informations sur les fichiers de configuration de stratégie de sécurité, consultez [à l’aide de Reporting Services Security Policy Files](../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).  
  
3.  Déclarez les autorisations requises dans le cadre de la méthode utilisée pour effectuer l'appel sécurisé. Cela est nécessaire car le code de l’assembly personnalisé qui est appelé par le serveur de rapports fait partie de l’assembly hôte d’expressions rapport, qui s’exécute avec **exécution** autorisation par défaut. Le **exécution** jeu d’autorisations permet au code à exécuter, mais ne pas d’utiliser des ressources protégées.  
  
4.  Marquer l’assembly personnalisé avec **AllowPartiallyTrustedCallersAttribute** s’il est signé avec un nom fort. Cela est nécessaire car les assemblys personnalisés sont appelées à partir d’une expression de rapport qui fait partie de l’assembly hôte d’expressions rapport, qui, par défaut, n’est pas accordée **FullTrust**; il est donc un appelant « niveau de confiance partiel ». Pour plus d’informations, consultez [les assemblys avec nom fort personnalisé](../../reporting-services/custom-assemblies/using-strong-named-custom-assemblies.md).  
  
## <a name="implementing-a-secure-call"></a>Implémentation d'un appel sécurisé  
 Vous pouvez modifier les fichiers de configuration de stratégie de manière à accorder des autorisations spécifiques à votre assembly. Par exemple, si vous écrivez un assembly personnalisé pour gérer la conversion de devises, vous aurez peut-être besoin de lire le taux de change de la devise actuelle dans un fichier. Pour récupérer les informations de fréquence, vous devez ajouter une autorisation de sécurité supplémentaire, **FileIOPermission**, pour le jeu d’autorisations de l’assembly. Vous pouvez ajouter l'entrée suivante au fichier de configuration de stratégie :  
  
```  
<PermissionSet class="NamedPermissionSet"  
   version="1"  
   Name="CurrencyRatesFilePermissionSet"  
   Description="A special permission set that grants read access to my currency rates file.">  
      <IPermission class="FileIOPermission"  
         version="1"  
         Read="C:\CurrencyRates.xml"/>  
      <IPermission class="SecurityPermission"  
         version="1"  
         Flags="Execution, Assertion"/>  
</PermissionSet>  
```  
  
 Vous pouvez ensuite ajouter une groupe de code qui référence ce jeu d'autorisations :  
  
```  
<CodeGroup class="UnionCodeGroup"  
   version="1"  
   PermissionSetName="CurrencyRatesFilePermissionSet"  
   Name="MyNewCodeGroup"  
   Description="A special code group for my custom assembly.">  
   <IMembershipCondition class="UrlMembershipCondition"  
      version="1"  
      Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\MSSQL\Reporting Services\ReportServer\bin\CurrencyConversion.dll"/>  
</CodeGroup>  
```  
  
 Pour que votre code acquière l'autorisation appropriée, vous devez déclarer cette autorisation dans le code de votre assembly personnalisé. Par exemple, si vous souhaitez ajouter l'accès en lecture seule à un fichier XML, C:\CurrencyRates.xml, vous devez ajouter le code suivant à votre méthode :  
  
```  
// C#  
FileIOPermission permission = new FileIOPermission(FileIOPermissionAccess.Read, @"C:\CurrencyRates.xml");  
try  
{  
   permission.Assert();  
   // Load the XML currency rates file  
   XmlDocument doc = new XmlDocument();  
   doc.Load(@"C:\CurrencyRates.xml");  
...  
```  
  
 Vous pouvez déclarer cette autorisation sous la forme d'un attribut de méthode :  
  
```  
[FileIOPermissionAttribute(SecurityAction.Assert, Read=@"C:\CurrencyRates.xml")]  
```  
  
 Pour plus d'informations, consultez la rubrique « Sécurité du .NET Framework » dans le Guide du développeur .NET Framework.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d'assemblages personnalisés avec des rapports](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
