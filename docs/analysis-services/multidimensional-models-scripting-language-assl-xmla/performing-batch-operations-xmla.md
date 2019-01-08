---
title: Exécution d’opérations de traitement par lots (XMLA) | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6c451d13016915c9218efb2963429f8f5a7709e2
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52544234"
---
# <a name="performing-batch-operations-xmla"></a>Exécution d'opérations de traitement par lot (XMLA)
  Vous pouvez utiliser la [Batch](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla) commande XML for Analysis (XMLA) pour exécuter plusieurs commandes XMLA à l’aide d’un seul XMLA [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) (méthode). Vous pouvez exécuter plusieurs commandes contenues dans le **Batch** commande comme une transaction unique ou dans des transactions individuelles pour chaque commande, en série ou en parallèle. Vous pouvez également spécifier des liaisons hors ligne et autres propriétés dans le **Batch** commande pour traiter plusieurs [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objets.  
  
## <a name="running-transactional-and-nontransactional-batch-commands"></a>Exécution de commandes Batch transactionnelles et non transactionnelles  
 Le **Batch** commande exécute les commandes de deux manières :  
  
 **Transactionnelle**  
 Si le **Transaction** attribut de la **Batch** du jeu de commandes sur true, le **Batch** commande exécute toutes les commandes que contient le **Batch** commande dans une seule transaction, un *transactionnelle* batch.  
  
 Si une commande échoue dans un lot transactionnel, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] annule les commandes le **Batch** commande exécutée avant la commande qui a échoué et le **Batch** commande se termine immédiatement. Toutes les commandes dans le **Batch** commande qui n’ont pas encore été exécutée ne sont pas exécutées. Après le **Batch** commande se termine, le **Batch** commande signale toutes les erreurs qui se sont produites pour la commande qui a échoué.  
  
 **Nontransactional**  
 Si le **Transaction** attribut est défini sur false, le **Batch** commande s’exécute chaque commande contenue par le **Batch** commande dans une transaction distincte  *non transactionnel* batch. Si une commande échoue dans un lot non transactionnel, la **Batch** commande continue à s’exécuter de commandes après la commande qui a échoué. Après le **Batch** commande tente d’exécuter toutes les commandes qui la **Batch** contient de la commande, le **Batch** commande signale toutes les erreurs qui se sont produites.  
  
 Tous les résultats retournés par les commandes contenues dans un **Batch** commande sont retournés dans le même ordre que celui dans lequel les commandes sont contenus dans le **Batch** commande. Les résultats retournés par une **Batch** commande varient selon que le **Batch** commande est transactionnelle ou non transactionnelle.  
  
> [!NOTE]  
>  Si un **Batch** commande contient une commande qui ne retourne pas de sortie, tels que le [verrou](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla) commande, et que commande s’exécute avec succès, le **Batch** commande retourne un vide [racine](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla) élément dans l’élément de résultats. Vide **racine** élément garantit que chaque commande contenue dans un **Batch** commande peut être mis en correspondance avec le bon **racine** , élément pour les résultats de cette commande.  
  
### <a name="returning-results-from-transactional-batch-results"></a>Retour des résultats d'un lot transactionnel  
 Résultats des commandes exécutées dans un lot transactionnel ne sont pas retournés jusqu'à ce que l’intégralité de **Batch** commande est terminée. Les résultats ne sont pas retournés après chaque commande s’exécute, car toute commande qui échoue dans un lot transactionnel serait provoque l’intégralité de **Batch** commande et toutes les commandes qu’elle contient est restaurée. Si toutes les commandes Démarrer et exécuter avec succès, le [retourner](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/return-element-xmla) élément de la [ExecuteResponse](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects-executeresponse) élément retourné par la **Execute** méthode pour le **Batch**  commande contient un [résultats](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/results-element-xmla) élément, qui à son tour contient un **racine** élément pour chaque commande correctement exécutée contenue dans le **Batch** commande. Si la commande le **Batch** commande ne peut pas être démarrée ou ne parvient pas à terminer, le **Execute** méthode retourne une erreur SOAP pour le **Batch** commande qui contient l’erreur de la commande qui a échoué.  
  
### <a name="returning-results-from-nontransactional-batch-results"></a>Retour des résultats d'un lot non transactionnel  
 Résultats des commandes exécutées dans un lot non transactionnel sont retournés dans l’ordre dans lequel les commandes sont contenues dans le **Batch** commande et comme ils sont retournés par chaque commande. Si aucune commande contenue dans le **Batch** commande peut être démarrée, le **Execute** méthode retourne une erreur SOAP qui contient une erreur pour le **Batch** commande. Si au moins une commande a démarré correctement, le **retourner** élément de la **ExecuteResponse** élément retourné par la **Execute** méthode pour le **Batch**  commande contient un **résultats** élément, qui à son tour contient un **racine** élément pour chaque commande contenue dans le **Batch** commande . Si une ou plusieurs commandes dans un lot non transactionnel ne peut pas être démarrés ou ne parvient pas à terminer, le **racine** élément pour la commande ayant échouée contient un [erreur](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla) élément décrivant l’erreur.  
  
> [!NOTE]  
>  Tant qu’au moins une commande dans un lot non transactionnel peut être démarrée, le lot non transactionnel est considérée comme avoir exécuté avec succès, même si chaque commande contenue dans le lot non transactionnel retourne une erreur dans les résultats de la **Batch**  commande.  
  
## <a name="using-serial-and-parallel-execution"></a>Utilisation d'une exécution en série et parallèle  
 Vous pouvez utiliser la **Batch** commande à exécuter inclus commandes en série ou en parallèle. Lorsque les commandes sont exécutées en série, la commande suivante incluse dans le **Batch** commande ne peut pas démarrer tant que la commande en cours d’exécution dans le **Batch** commande est terminée. Lorsque les commandes sont exécutées en parallèle, plusieurs commandes peuvent être exécutées simultanément par le **Batch** commande.  
  
 Pour exécuter des commandes en parallèle, vous ajoutez les commandes à exécuter en parallèle pour le [parallèles](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/parallel-element-xmla) propriété de la **Batch** commande. Actuellement, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] peut exécuter uniquement contiguës et séquentielles [processus](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) commandes en parallèle. Les autres commandes XMLA, tel que [créer](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) ou [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla), inclus dans le **parallèles** propriété est exécutée en série.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tente d’exécuter tous les **processus** commandes incluses dans le **parallèles** propriété en parallèle, mais ne peut pas garantir que toutes les inclus **processus** commandes peuvent être exécutées en parallèle. L’instance analyse chaque **processus** commande et, si l’instance détermine que la commande ne peut pas être exécutée en parallèle, le **processus** commande est exécutée en série.  
  
> [!NOTE]  
>  Pour exécuter des commandes en parallèle, le **Transaction** attribut de la **Batch** commande doit être définie sur true, car [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] prend en charge qu’une seule transaction active par connexion et non transactionnelles lots exécutés chaque commande dans une transaction distincte. Si vous incluez le **parallèles** propriété dans un lot non transactionnel, une erreur se produit.  
  
### <a name="limiting-parallel-execution"></a>Limitation de l'exécution parallèle  
 Un [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance tente d’exécuter autant **processus** commandes en parallèle que possible, jusqu’aux limites de l’ordinateur sur lequel s’exécute l’instance. Vous pouvez limiter le nombre d’exécution simultanément **processus** commandes en définissant le **maxParallel** attribut de la **parallèles** propriété à une valeur indiquant le nombre maximal de **processus** commandes qui peuvent être exécutés en parallèle.  
  
 Par exemple, un **parallèles** propriété contient les commandes suivantes dans l’ordre indiqué :  
  
1.  **Créer**  
  
2.  **Traiter**  
  
3.  **Alter**  
  
4.  **Traiter**  
  
5.  **Traiter**  
  
6.  **Traiter**  
  
7.  **Supprimer**  
  
8.  **Traiter**  
  
9. **Traiter**  
  
 Le **maxParalle**attribut l de ce **parallèles** propriété est définie sur 2. Par conséquent, l'instance exécute les listes précédentes de commandes comme décrit dans la liste suivante :  
  
-   Commande 1 s’exécute en série, car la commande 1 est un **créer** commande et uniquement **processus** commandes peuvent être exécutées en parallèle.  
  
-   La commande 2 s'exécute en série une fois que la commande 1 a abouti.  
  
-   La commande 3 s'exécute en série une fois que la commande 2 a abouti.  
  
-   Les commandes 4 et 5 s'exécutent en parallèle une fois que la commande 3 a abouti. Bien que la commande 6 est également un **processus** commande, commande 6 ne peut pas s’exécuter en parallèle avec les commandes 4 et 5, car le **maxParallel** propriété est définie sur 2.  
  
-   La commande 6 s'exécute en série une fois que les commandes 4 et 5 ont abouti.  
  
-   La commande 7 s'exécute en série une fois que la commande 6 a abouti.  
  
-   Les commandes 8 et 9 s'exécutent en parallèle une fois que la commande 7 a abouti.  
  
## <a name="using-the-batch-command-to-process-objects"></a>Utilisation de la commande Batch pour traiter les objets  
 Le **Batch** commande contient plusieurs propriétés et attributs facultatifs spécifiquement inclus pour prendre en charge de traitement multiple [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] projets :  
  
-   Le **ProcessAffectedObjects** attribut de la **Batch** commande indique si l’instance doit également traiter les objets qui nécessitent le retraitement à la suite d’un **processus** commande inclus dans le **Batch** commande de traitement d’un objet spécifié.  
  
-   Le [liaisons](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla) propriété constituée une collection de liaisons hors ligne utilisée par toutes les **processus** commandes dans le **Batch** commande.  
  
-   Le [DataSource](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasource-element-xmla) propriété contient une liaison hors ligne pour une source de données utilisée par toutes les **processus** commandes dans le **Batch** commande.  
  
-   Le [DataSourceView](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla) propriété contient une liaison hors ligne pour une vue de source de données utilisée par toutes les **processus** commandes dans le **Batch** commande.  
  
-   Le [ErrorConfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla) propriété spécifie la manière dont le **Batch** commande gère les erreurs rencontrées par tous les **processus** commandes contenues dans le **Batch** commande.  
  
    > [!IMPORTANT]  
    >  Un **processus** commande ne peut pas inclure le **liaisons**, **DataSource**, **DataSourceView**, ou **ErrorConfiguration**  propriétés, si le **processus** commande est contenue dans un **Batch** commande. Si vous devez spécifier ces propriétés pour un **processus** commande, fournissez les informations nécessaires dans les propriétés correspondantes de la **Batch** commande qui contient le **processus** commande.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément du lot &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla)   
 [Traiter l’élément &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla)   
 [Traitement d’un modèle multidimensionnel &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)   
 [Développement avec XMLA dans Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
