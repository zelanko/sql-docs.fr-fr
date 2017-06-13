---
title: "Accès aux assemblys personnalisés via des Expressions | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
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
- expressions [Reporting Services], custom assemblies
- static member calls
- instance member calls [Reporting Services]
- calling class members
- custom assemblies [Reporting Services], expressions
ms.assetid: 917c4d47-1a95-4f54-98b1-e8cb2165d90f
caps.latest.revision: 32
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 70ff488827e5289d401bf62b67a82a08ecc25f70
ms.contentlocale: fr-fr
ms.lasthandoff: 06/13/2017

---
# <a name="accessing-custom-assemblies-through-expressions"></a>Accès aux assemblys personnalisés par le biais d'expressions
  Une fois que vous avez créé un assembly personnalisé, qu'il est disponible auprès du Concepteur de rapports ou du serveur de rapports, que vous avez ajouté la stratégie de sécurité appropriée et une référence à votre assembly personnalisé dans votre définition de rapport, vous pouvez accéder aux membres des classes dans votre assembly à l'aide d'expressions de rapport. Pour faire référence à du code personnalisé dans une expression, vous devez appeler le membre d'une classe au sein de l'assembly. La procédure pour ce faire dépend du type de méthode, à savoir statique ou basée sur une instance.  
  
## <a name="calling-static-members-from-a-report-definition-file"></a>Appel de membres statiques d'un fichier de définition de rapport  
 Les membres statiques appartiennent à la classe ou au type, pas à un objet instancié. Ces membres sont accessibles en les appelant directement depuis la classe. Vous devez utiliser des membres statiques pour appeler des fonctions personnalisées dans un rapport chaque fois que possible, parce que les membres statiques offrent de meilleures performances. Pour appeler un membre statique, vous devez le référencer comme une expression qui prend la forme =*Namespace.Class.Method*.  
  
#### <a name="to-call-static-members"></a>Pour appeler des membres statiques  
  
-   Pour appeler un membre statique, définissez votre expression pour qu'elle soit égale au nom complet du membre, à savoir l'espace de noms, le nom de classe et le nom de membre. L’exemple suivant appelle la **ToGBP** (méthode), qui convertit le **StandardCost** champ de valeur de dollars en livres sterling et l’affiche dans un rapport :  
  
    ```  
    =CurrencyConversion.DollarCurrencyConversion.ToGBP(Fields!StandardCost.Value)  
    ```  
  
### <a name="important-information-regarding-static-fields-and-properties"></a>Informations importantes concernant les champs et les propriétés statiques  
 Actuellement, tous les rapports sont exécutés dans le même domaine d'application. Cela signifie que les rapports contenant des données statiques spécifiques à l'utilisateur exposent ces données à d'autres instances du même rapport. Cette condition peut permettre aux données statiques d'un utilisateur d'être disponibles pour tous les utilisateurs qui exécutent actuellement un rapport particulier. Pour cette raison, il est recommandé que vous N'utilisez pas les champs statiques ou des propriétés dans des assemblys personnalisés ou dans le **Code** élément ; utilisez plutôt des propriétés ou champs d’instance dans vos rapports. Les méthodes statiques peuvent encore être utilisées car elles ne stockent pas d'état ou de données.  
  
## <a name="calling-instance-members-from-a-report-definition-file"></a>Appel de membres d'instance à partir d'un fichier de définition de rapport  
 Si votre assembly personnalisé contient des membres d'instance auxquels vous devez accéder dans une définition de rapport, vous devez ajouter un nom d'instance pour votre classe au rapport. Vous pouvez ajouter un nom d’instance pour une classe qui utilise le **Code** onglet de la **propriétés de rapport** boîte de dialogue. Pour plus d’informations sur l’ajout d’instances de classes à un rapport, consultez [Code personnalisé et références d’Assembly dans les Expressions dans le Concepteur de rapports &#40; SSRS &#41; ](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
 Pour appeler un membre statique, vous devez le référencer comme une expression qui prend la forme = Code*. InstanceName.Method*.  
  
#### <a name="to-call-instance-members"></a>Pour appeler des membres d'instance  
  
-   Pour appeler un membre d’instance d’un assembly personnalisé, vous devez référencer le **Code** mot clé suivi par le nom d’instance et de la méthode. L’exemple suivant appelle une méthode d’instance **ToEUR** qui convertit le **StandardCost** champ de valeur de dollars en euros et l’affiche dans un rapport :  
  
    ```  
    =Code.m_myDollarCoversion.ToEUR(Fields!StandardCost.Value)  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’assemblys personnalisés avec des rapports](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
