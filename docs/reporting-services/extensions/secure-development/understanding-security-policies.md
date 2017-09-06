---
title: "Présentation des stratégies de sécurité | Documents Microsoft"
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
- code groups [Reporting Services]
- code access security [Reporting Services], security policies
- Execution permission set
- custom assemblies [Reporting Services], security
- permission sets [Reporting Services]
- expressions [Reporting Services], security
- evidence [Reporting Services]
- FullTrust permission set
- security policies [Reporting Services]
- named permission sets [Reporting Services]
ms.assetid: a9bf043a-139a-4929-9a58-244815323df0
caps.latest.revision: 32
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 4c8fa977e2b9cdd596e3029be4954daea7fe239d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/12/2017

---
# <a name="understanding-security-policies"></a>Présentation des stratégies de sécurité
  Tout code exécuté par un serveur de rapports doit faire partie d'une stratégie de sécurité d'accès du code spécifique. Ces stratégies de sécurité comprennent des groupes de codes qui mappent une preuve à un ensemble de jeux d'autorisations nommés. Souvent, les groupes de codes sont associés à un jeu d'autorisations nommé qui spécifie les autorisations pouvant être accordées au code dans ce groupe. Le runtime utilise la preuve fournie par un hôte approuvé ou par le chargeur pour déterminer les groupes de codes auxquels le code appartient et, par conséquent, les autorisations à accorder au code. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]adhère à cette architecture de stratégie de sécurité, tel que défini par le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] common language runtime (CLR). Les sections suivantes décrivent les divers types de codes qui existent dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], ainsi que les règles de stratégie associées.  
  
## <a name="report-server-assemblies"></a>Assemblys du serveur de rapports  
 Les assemblys du serveur de rapports sont ceux qui contiennent du code faisant partie du produit [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] est écrit à l'aide d'assemblys de code managé ; tous ces assemblys portent un nom fort (autrement dit, ils sont signés numériquement). Les groupes de codes de ces assemblys sont définis à l’aide de la **StrongNameMembershipCondition**, ce qui constitue une preuve basée sur les informations de clé publique de nom fort de l’assembly. Le groupe de codes est accordé le **FullTrust** jeu d’autorisations.  
  
## <a name="report-server-extensions-rendering-data-delivery-and-security"></a>Extensions du serveur de rapports (rendu, données, remise et sécurité)  
 Les extensions du serveur de rapports sont des extensions personnalisées en matière de données, de remise, de rendu et de sécurité que vous ou des personnes tierces créez afin d'étendre les fonctionnalités de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Vous devez accorder **FullTrust** à ces extensions ou au code assembleur dans les fichiers de configuration de stratégie associé à le [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] composant que vous étendez. Extensions fournies dans le cadre de [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] sont signés avec la clé publique de serveur de rapports et de recevoir le **FullTrust** jeu d’autorisations.  
  
> [!IMPORTANT]  
>  Vous devez modifier le [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] fichiers de configuration de stratégie pour autoriser **FullTrust** pour toutes les extensions de tiers. Si vous n’ajoutez pas d’un groupe de codes avec **FullTrust** pour vos extensions personnalisées, ils ne peuvent pas être utilisés par le serveur de rapports.  
  
 Pour plus d’informations sur les fichiers de configuration de stratégie dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], consultez [à l’aide de Reporting Services Security Policy Files](../../../reporting-services/extensions/secure-development/using-reporting-services-security-policy-files.md).  
  
## <a name="expressions-used-in-reports"></a>Expressions utilisées dans les rapports  
 Les expressions de rapport sont des expressions de code inline ou des méthodes définies par l’utilisateur dans le **Code** élément d’un fichier de langage de définition de rapport. Il existe un groupe de codes qui est déjà configuré dans les fichiers de stratégie qui accorde ces expressions le **exécution** autorisation avec la valeur par défaut. Le groupe de codes ressemble à ceci :  
  
```  
<CodeGroup  
   class="UnionCodeGroup"  
   version="1"  
   PermissionSetName="Execution"  
   Name="Report_Expressions_Default_Permissions"  
   Description="This code group grants default permissions for code in report expressions and Code element. ">  
    <IMembershipCondition  
       class="StrongNameMembershipCondition"  
       version="1"  
       PublicKeyBlob="002400..."  
    />  
</CodeGroup>  
```  
  
 **L’exécution** autorisation permet au code d’exécution (execute), mais ne pas pour utiliser des ressources protégées. Toutes les expressions d'un rapport sont compilées en un assembly (appelé assembly « hôte d'expressions ») qui est stocké en tant que partie du rapport compilé. Lorsque le rapport est exécuté, le serveur de rapports charge l'assembly hôte d'expressions et effectue des appels dans cet assembly pour exécuter les expressions. Les assemblys hôtes d'expressions sont signés avec une clé spécifique utilisée pour définir le groupe de codes de tous les hôtes d'expressions.  
  
 Les expressions de rapport référencent des collections du modèle objet de rapport (champs, paramètres, etc.) et effectuent des tâches simples comme l'arithmétique et des opérations de chaîne. Le code qui effectue ces opérations simples requiert uniquement **exécution** autorisation. Par défaut, les méthodes définies par l’utilisateur dans le **Code** élément et tous les assemblys personnalisés sont accordés **exécution** autorisation dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Par conséquent, pour la plupart des expressions, la configuration actuelle ne requiert pas que vous modifiiez les fichiers de stratégie de sécurité. Pour accorder des autorisations supplémentaires aux assemblys hôtes d'expressions, un administrateur doit modifier les fichiers de configuration de stratégie du serveur de rapports et du Concepteur de rapports ; en outre, il doit également modifier le groupe de codes des expressions de rapport. Dans la mesure où il s'agit d'un paramètre global, la modification des autorisations par défaut des hôtes d'expressions affecte tous les rapports. Pour cette raison, il est vivement recommandé que vous placiez l'ensemble du code qui requiert une sécurité supplémentaire dans un assembly personnalisé. Seul cet assembly recevra les autorisations dont vous avez besoin.  
  
> [!IMPORTANT]  
>  Le code qui appelle des assemblys externes ou des ressources protégées doit être incorporé dans un assembly personnalisé à utiliser dans les rapports. Vous disposez ainsi d'un plus grand contrôle des autorisations requises et déclarées par votre code. N’effectuez pas les appels à sécuriser des méthodes dans le **Code** élément. Cela vous oblige à accorder **FullTrust** à l’hôte d’expressions de rapport et accorde à tout le code personnalisé complet d’accès au CLR.  
  
> [!CAUTION]  
>  N’accordez pas **FullTrust** au groupe de codes pour un hôte d’expressions de rapport. Sinon, vous permettez à toutes les expressions de rapport d'effectuer des appels système protégés.  
  
## <a name="custom-assemblies-referenced-in-reports"></a>Assemblys personnalisés référencés dans les rapports  
 Certaines expressions de rapport peuvent appeler des assemblys de code tiers, également nommés assemblys personnalisés dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Le serveur de rapports attend ces assemblys sont censés disposer au moins **exécution** autorisation dans les fichiers de configuration de stratégie. Par défaut, les fichiers de stratégie fournis avec [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] accorder **exécution** autorisation à tous les assemblys à partir de la zone « Mon ordinateur ». Vous pouvez accorder des autorisations supplémentaires aux assemblys personnalisés en fonction de vos besoins.  
  
 Dans certains cas, vous devrez peut-être effectuer une opération qui requiert des autorisations de code spécifique dans une expression de rapport. En règle générale, cela signifie qu'une expression de rapport doit appeler une méthode de bibliothèque CLR sécurisée (par exemple une méthode de bibliothèque qui accède aux fichiers ou au Registre système). La documentation du [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] décrit les autorisations de code requises pour effectuer cet appel sécurisé ; pour exécuter l'appel, le code appelant doit recevoir ces autorisations sécurisées spécifiques. Si vous effectuez l’appel à partir d’une expression de rapport ou la **Code** élément, l’assembly hôte d’expressions doit être accordée les autorisations appropriées. Cependant, une fois que vous avez accordé les autorisations appropriées à l'hôte d'expressions, tout code s'exécutant dans l'expression d'un rapport reçoit désormais cette autorisation spécifique. Il est beaucoup plus sûr d'effectuer l'appel à partir d'un assembly personnalisé et d'accorder à ce dernier les autorisations spécifiques.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité d’accès du code dans Reporting Services](../../../reporting-services/extensions/secure-development/code-access-security-in-reporting-services.md)   
 [Sécuriser le développement &#40; Reporting Services &#41;](../../../reporting-services/extensions/secure-development/secure-development-reporting-services.md)  
  
  
