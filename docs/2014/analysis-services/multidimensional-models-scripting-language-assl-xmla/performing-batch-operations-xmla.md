---
title: Exécution d’opérations de traitement par lots (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- multiple projects
- XML for Analysis, batches
- parallel batch execution [XMLA]
- transactional batches
- serial batch execution [XMLA]
- XMLA, batches
- batches [XML for Analysis]
- nontransactional batches
ms.assetid: 731c70e5-ed51-46de-bb69-cbf5aea18dda
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2bd661506dbb792eb55194c61d7284d619e63a5f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62702061"
---
# <a name="performing-batch-operations-xmla"></a>Exécution d'opérations de traitement par lot (XMLA)
  Vous pouvez utiliser la commande [batch](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) dans XML for Analysis (XMLA) pour exécuter plusieurs commandes XMLA à l’aide d’une seule méthode XMLA [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) . Vous pouvez exécuter plusieurs commandes contenues dans la commande `Batch` sous la forme d'une transaction unique ou de plusieurs transactions individuelles pour chaque commande, en série ou en parallèle. Vous pouvez également spécifier des liaisons hors ligne et d’autres propriétés dans la commande pour `Batch` le traitement de plusieurs [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objets.  
  
## <a name="running-transactional-and-nontransactional-batch-commands"></a>Exécution de commandes Batch transactionnelles et non transactionnelles  
 La commande `Batch` peut exécuter les commandes selon deux modes :  
  
 **Transactionnelle**  
 Si l' `Transaction` attribut de la `Batch` commande est défini sur true, la `Batch` commande exécute toutes les commandes contenues par la `Batch` commande dans une transaction unique (un lot *transactionnel* ).  
  
 Si une commande échoue dans un lot transactionnel, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] restaure toute commande de la `Batch` commande exécutée avant la commande qui a échoué et la `Batch` commande se termine immédiatement. Les commandes contenues dans la commande `Batch` dont l'exécution n'a pas encore eu lieu ne sont pas exécutées. Une fois la commande `Batch` terminée, la commande `Batch` fait état des erreurs qui se sont produites pour la commande ayant échoué.  
  
 **Non transactionnel**  
 Si l' `Transaction` attribut a la valeur false, `Batch` la commande exécute chaque commande contenue `Batch` par la commande dans une transaction distincte, c’est-à-dire un lot non *transactionnel* . En cas d'échec d'une commande dans un lot non transactionnel, la commande `Batch` continue d'exécuter les commandes venant après la commande qui a échoué. Après avoir tenté d'exécuter toutes les `Batch` commandes contenues dans la commande `Batch`, la commande `Batch` fait état des erreurs qui se sont éventuellement produites.  
  
 Tous les résultats retournés par les commandes contenues dans une commande `Batch` sont retournés dans l'ordre qui est le leur dans la commande `Batch`. Les résultats retournés par une commande `Batch` varient selon que la commande `Batch` est transactionnelle ou non transactionnelle.  
  
> [!NOTE]  
>  Si une `Batch` commande contient une commande qui ne retourne pas de sortie, telle que la commande [Lock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) et que cette commande s’exécute correctement `Batch` , la commande retourne un élément [racine](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla) vide dans l’élément results. L'élément `root` vide garantit que chaque commande contenue dans une commande `Batch` peut être mise en correspondance avec l'élément `root` approprié pour les résultats de cette commande.  
  
### <a name="returning-results-from-transactional-batch-results"></a>Retour des résultats d'un lot transactionnel  
 Les résultats des commandes exécutées dans un lot transactionnel ne sont pas retournés tant que la commande `Batch` n'a pas abouti complètement. Les résultats ne sont pas retournés après l'exécution de chaque commande, car toute commande qui échoue dans un lot transactionnel entraîne l'annulation de la commande `Batch` entière et de toutes les commandes qu'elle contient. Si toutes les commandes démarrent et s’exécutent correctement, l’élément [Return](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/return-element-xmla) de l' `Execute` élément [ExecuteResponse](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects-executeresponse) retourné `Batch` par la méthode pour la commande contient un élément [results](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/results-element-xmla) , qui, à son tour, contient `root` un `Batch` élément pour chaque commande Run réussie contenue dans la commande. Si la commande `Batch` contient une commande qui ne peut pas démarrer ou aboutir, la méthode `Execute` retourne une erreur SOAP pour la commande `Batch` qui contient l'erreur de la commande qui a échoué.  
  
### <a name="returning-results-from-nontransactional-batch-results"></a>Retour des résultats d'un lot non transactionnel  
 Les résultats des commandes exécutées dans un lot non transactionnel sont retournés dans l'ordre qui est le leur dans la commande `Batch` et tels qu'ils sont retournés par chaque commande. Si, à l'intérieure de la commande `Batch`, aucune commande ne peut démarrer correctement, la méthode `Execute` retourne une erreur SOAP qui contient une erreur pour la commande `Batch`. Si au moins une commande a démarré correctement, l'élément `return` de l'élément `ExecuteResponse` retourné par la méthode `Execute` pour la commande `Batch` contient un élément `results` qui, pour sa part, contient un élément `root` pour chaque commande contenue dans la commande `Batch`. Si une ou plusieurs commandes d’un lot non transactionnel ne peuvent pas être démarrées ou ne se terminent pas, l’élément de la `root` commande qui a échoué contient un élément [Error](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla) décrivant l’erreur.  
  
> [!NOTE]  
>  Du moment où au moins une commande parvient à démarrer dans un lot non transactionnel, celui-ci est considéré comme s'étant exécuté correctement, même si chaque commande contenue dans le lot non transactionnel retourne une erreur dans les résultats de la commande `Batch`.  
  
## <a name="using-serial-and-parallel-execution"></a>Utilisation d'une exécution en série et parallèle  
 Vous pouvez utiliser la commande `Batch` pour exécuter les commandes qu'elle contient en série ou en parallèle. Lorsque les commandes sont exécutées en série, la commande suivante incluse dans la commande `Batch` ne peut pas démarrer tant que la commande en cours d'exécution dans la commande `Batch` n'a pas abouti. Lorsque les commandes sont exécutées en parallèle, plusieurs commandes peuvent être exécutées simultanément par la commande `Batch`.  
  
 Pour exécuter des commandes en parallèle, vous ajoutez les commandes à exécuter en parallèle à la propriété [Parallel](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/parallel-element-xmla) de la `Batch` commande. Actuellement, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] peut exécuter uniquement des commandes de [processus](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) séquentielles contiguës en parallèle. Toutes les autres commandes XMLA, telles que [Create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) ou [ALTER](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla), incluses `Parallel` dans la propriété sont exécutées en série.  
  
 
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] essaie d'exécuter en parallèle toutes les commandes `Process` incluses dans la propriété `Parallel`, mais ne peut pas garantir que toutes les commandes `Process` incluses puissent être exécutées en parallèle. L'instance analyse chaque commande `Process`. Si elle détermine qu'une commande `Process` ne peut pas être exécutée en parallèle, elle est exécutée en série.  
  
> [!NOTE]  
>  Pour exécuter des commandes en parallèle, l'attribut `Transaction` de la commande `Batch` doit être défini à true, car [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne prend en charge qu'une seule transaction active par connexion et les lots non transactionnels exécutent chaque commande dans une transaction distincte. Si vous incluez la propriété `Parallel` dans un lot non transactionnel, une erreur se produit.  
  
### <a name="limiting-parallel-execution"></a>Limitation de l'exécution parallèle  
 Une instance [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] essaie d'exécuter autant de commandes `Process` en parallèle que possible, dans les limites de l'ordinateur sur lequel s'exécute l'instance. Vous pouvez limiter le nombre de commandes `Process` pouvant s'exécuter simultanément en définissant l'attribut `maxParallel` de la propriété `Parallel` avec une valeur indiquant le nombre maximal de commandes `Process` qui peuvent être exécutées en parallèle.  
  
 Par exemple, une propriété `Parallel` contient les commandes suivantes dans l'ordre indiqué :  
  
1.  `Create`  
  
2.  `Process`  
  
3.  `Alter`  
  
4.  `Process`  
  
5.  `Process`  
  
6.  `Process`  
  
7.  `Delete`  
  
8.  `Process`  
  
9. `Process`  
  
 L'attribut `maxParalle` de cette propriété `Parallel` est défini à 2. Par conséquent, l'instance exécute les listes précédentes de commandes comme décrit dans la liste suivante :  
  
-   La commande 1 s'exécute en série, car la commande 1 est une commande `Create` et seules les commandes `Process` peuvent être exécutées en parallèle.  
  
-   La commande 2 s'exécute en série une fois que la commande 1 a abouti.  
  
-   La commande 3 s'exécute en série une fois que la commande 2 a abouti.  
  
-   Les commandes 4 et 5 s'exécutent en parallèle une fois que la commande 3 a abouti. Bien que la commande 6 soit également une commande `Process`, elle ne peut pas s'exécuter en parallèle avec les commandes 4 et 5, car la propriété `maxParallel` est définie à 2.  
  
-   La commande 6 s'exécute en série une fois que les commandes 4 et 5 ont abouti.  
  
-   La commande 7 s'exécute en série une fois que la commande 6 a abouti.  
  
-   Les commandes 8 et 9 s'exécutent en parallèle une fois que la commande 7 a abouti.  
  
## <a name="using-the-batch-command-to-process-objects"></a>Utilisation de la commande Batch pour traiter les objets  
 La commande `Batch` contient plusieurs propriétés et attributs facultatifs qui ont été spécifiquement inclus pour prendre en charge le traitement de plusieurs projets [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] :  
  
-   L'attribut `ProcessAffectedObjects` de la commande `Batch` indique si l'instance doit également traiter les objets qui nécessitent un retraitement du fait de l'inclusion d'une commande `Process` dans la commande `Batch` traitant un objet spécifié.  
  
-   La propriété [bindings](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla) contient une collection de liaisons hors ligne utilisées par toutes les `Process` commandes dans la `Batch` commande.  
  
-   La propriété [DataSource](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) contient une liaison hors ligne pour une source de données utilisée par toutes les `Process` commandes dans la `Batch` commande.  
  
-   La propriété [DataSourceView](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla) contient une liaison hors ligne pour une vue de source de données utilisée par toutes les `Process` commandes dans la `Batch` commande.  
  
-   La propriété [ErrorConfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla) spécifie la façon dont la `Batch` commande gère les erreurs rencontrées `Process` par toutes les commandes `Batch` contenues dans la commande.  
  
    > [!IMPORTANT]  
    >  Une commande `Process` ne peut pas comporter les propriétés `Bindings`, `DataSource`, `DataSourceView` ou `ErrorConfiguration` si la commande `Process` est contenue dans une commande `Batch`. Si vous devez spécifier ces propriétés pour une commande `Process`, fournissez les informations nécessaires dans les propriétés correspondantes de la commande `Batch` qui contient la commande `Process`.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément batch &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla)   
 [Élément process &#40;&#41;XMLA](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla)   
 [Traitement d’objets de modèle multidimensionnel](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md)   
 [Développement avec XMLA dans Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
