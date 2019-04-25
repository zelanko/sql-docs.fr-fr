---
title: Le Mode DirectQuery (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.realtime.f1
ms.assetid: 45ad2965-05ec-4fb1-a164-d8060b562ea5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9226a15351e8c6fcc938543d04fc95b0237f702b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62757372"
---
# <a name="directquery-mode-ssas-tabular"></a>Mode DirectQuery (SSAS Tabulaire)
  Analysis Services vous permet de récupérer des données et de créer des rapports à partir d'un modèle tabulaire en récupérant des données et des agrégats directement à partir d'un système de base de données relationnelle, à l'aide du *mode DirectQuery*. Cette rubrique présente les différences entre les modèles tabulaires standard qui résident uniquement en mémoire et les modèles tabulaires qui peuvent interroger une source de données relationnelle, et explique comment créer et déployer un modèle utilisable en mode DirectQuery.  
  
 Sections de cette rubrique :  
  
-   [Avantages du Mode DirectQuery](#bkmk_Benefits)  
  
-   [Création de modèles pour une utilisation avec le Mode DirectQuery](#bkmk_Design)  
  
    -   [Sources de données pour les modèles DirectQuery](directquery-mode-ssas-tabular.md#bkmk_DataSources)  
  
    -   [Restrictions de validation et conception pour le Mode DirectQuery](#bkmk_Validation)  
  
    -   [Compatibilité des formules pour les modèles DirectQuery](#bkmk_FormulaCompat)  
  
    -   [Sécurité en Mode DirectQuery](#bkmk_Security)  
  
    -   [Sécurité en Mode DirectQuery](#bkmk_Security)  
  
-   [Propriétés DirectQuery](#bkmk_PropertyList)  
  
-   [Tâches et rubriques connexes](#bkmk_related_tasks)  
  
##  <a name="bkmk_Benefits"></a> Avantages du Mode DirectQuery  
 Par défaut, les modèles tabulaires utilisent un cache mémoire pour stocker et interroger les données. Étant donné que les modèles tabulaires utilisent des données qui résident dans la mémoire, même les requêtes complexes peuvent être extrêmement rapides. Toutefois, l'utilisation de données en mémoire cache présente des inconvénients :  
  
-   Les données ne sont pas actualisées lorsque des modifications sont apportées aux données sources. Vous devez traiter le modèle pour obtenir les mises à jour des données.  
  
-   Lorsque vous arrêtez l'ordinateur qui héberge le modèle, le cache est enregistré sur le disque et doit être rouvert lorsque vous chargez le modèle ou ouvrez le fichier PowerPivot. Les opérations de sauvegarde et de chargement peuvent être longues.  
  
 Par opposition, le mode DirectQuery utilise des données stockées dans une base de données SQL Server.  En général, vous importez toutes les données ou un petit échantillon de données dans le cache lorsque vous créez le modèle, et lorsque vous déployez le modèle, vous spécifiez que la source de données des requêtes sur le modèle doit être SQL Server, et non pas les données en cache. Toutes les requêtes DAX sur les données sont converties par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] en instructions SQL équivalentes sur la source de données relationnelle spécifiée.  
  
 Le déploiement d'un modèle à l'aide du mode DirectQuery présente de nombreux avantages :  
  
-   Il permet d'utiliser un modèle pour les ensembles de données qui sont trop volumineux pour tenir dans la mémoire du serveur Analysis Services.  
  
-   Les données sont à jour, et il n'y a aucune charge de gestion supplémentaire liée à la conservation d'une copie distincte des données. Les modifications apportées aux données sources sous-jacentes peuvent être immédiatement reflétées dans des requêtes sur le modèle de données.  
  
-   DirectQuery peut tirer parti de l'accélération des requêtes côté fournisseur, telle que celle fournie par les index de colonne optimisés en mémoire xVelocity.  
  
-   Toute sécurité imposée par la base de données principale est appliquée, à l'aide de la sécurité au niveau des lignes. En revanche, si vous utilisez des données en mémoire cache, il peut être difficile de garantir que le cache est sécurisé exactement comme sur le serveur.  
  
-   Si le modèle contient des formules complexes qui peuvent nécessiter plusieurs requêtes, Analysis Services peut procéder à une optimisation pour garantir que le plan de requête pour la requête exécutée sur la base de données principale est aussi efficace que possible.  
  
##  <a name="bkmk_Design"></a> Création de modèles pour une utilisation avec le Mode DirectQuery  
 Les modèles tabulaires sont créés à l'aide du concepteur de modèles [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Le concepteur du modèle crée tous les modèles dans la mémoire, ce qui signifie que lorsque vous modélisez, si vos données sont trop volumineuses pour tenir dans la mémoire, vous devez importer uniquement un sous-ensemble de données dans le cache utilisé par la base de données de l'espace de travail.  
  
 Lorsque vous êtes prêt à passer en mode DirectQuery, vous pouvez modifier une propriété qui active le mode DirectQuery. Pour plus d’informations, consultez [activer le Mode Création DirectQuery &#40;tabulaire SSAS&#41;](enable-directquery-mode-in-ssdt.md).  
  
 Lorsque vous effectuez cette opération, le concepteur de modèles configure automatiquement la base de données de l'espace de travail pour qu'elle s'exécute en mode hybride, ce qui vous permet de continuer à utiliser les données en mémoire cache. Le concepteur de modèles vous informera également de toutes les fonctionnalités de votre modèle qui ne sont pas compatibles avec le mode DirectQuery. La liste suivante résume les principales conditions requises à garder à l'esprit :  
  
-   **Sources de données :** Les modèles DirectQuery peuvent uniquement utiliser des données d’une source de données SQL Server. Lorsque le mode DirectQuery a été activé pour un modèle, vous ne pouvez utiliser aucun autre type de données dans le concepteur de modèles, y compris les tables ajoutées par les opérations de copier-coller. Toutes les autres options d'importation sont désactivées. Toute table incluse dans une requête doit faire partie de la source de données SQL Server. Pour plus d'informations, consultez [Data Sources for DirectQuery Models](directquery-mode-ssas-tabular.md#bkmk_DataSources).  
  
-   **Prise en charge pour les colonnes calculées :** Les colonnes calculées ne sont pas pris en charge pour les modèles DirectQuery. Toutefois, vous pouvez créer des mesures et des indicateurs de performance clés, qui s'exécutent sur des ensembles de données. Pour plus d'informations, consultez la section relative à la [validation](#bkmk_Validation) .  
  
-   **Utilisation limitée des fonctions DAX :** Certaines fonctions DAX ne peut pas être utilisées en mode DirectQuery, vous devez donc les remplacer par d’autres fonctions, ou créez les valeurs à l’aide de colonnes dérivées dans la source de données. Le concepteur de modèles assure la validation au moment de la conception pour toutes les erreurs qui surviennent lorsque vous créez des formules qui ne sont pas compatibles avec le mode DirectQuery. Consultez les sections suivantes pour plus d’informations : [Validation](#bkmk_Validation).  
  
-   **Compatibilité des formules :** dans certains cas connus, la même formule peut retourner différents résultats dans un modèle mis en cache ou hybride comparé à un modèle DirectQuery qui utilise uniquement la banque de données relationnelle. Ces différences sont une conséquence des différences sémantiques entre le moteur d'analyse en mémoire xVelocity (VertiPaq) et SQL Server. Pour plus d’informations sur ces différences, consultez cette section : [Compatibilité des formules](#bkmk_FormulaCompat).  
  
-   **Sécurité :** Vous pouvez utiliser différentes méthodes pour sécuriser les modèles en fonction de la manière dont ils sont déployés. Les données mises en cache pour les modèles tabulaires sont sécurisées à l'aide du modèle de sécurité de l'instance Analysis Services. Les modèles DirectQuery peuvent être sécurisés à l'aide de rôles, mais vous pouvez également utiliser la sécurité définie dans la banque de données relationnelle. Le modèle peut être configuré de sorte que les utilisateurs qui ouvrent un rapport basé sur un modèle DirectQuery puissent uniquement voir les données que leurs autorisations dans SQL Server leur permettent de voir. Consultez cette section pour plus d’informations : [Sécurité](#bkmk_Security).  
  
-   **Restrictions client :** Lorsqu’un modèle est en mode DirectQuery, il ne peut être interrogé à l’aide de DAX. Vous ne pouvez pas utiliser MDX pour créer des requêtes. Cela signifie que vous ne pouvez pas utiliser le client de tableau croisé dynamique Excel, car Excel utilise MDX.  
  
     Toutefois, vous pouvez créer des requêtes sur un modèle DirectQuery dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] si vous utilisez une requête de table DAX dans le cadre d’une instruction XMLA Execute, pour plus d’informations, consultez [référence syntaxique des requêtes DAX](https://msdn.microsoft.com/library/ee634217.aspx).  
  
 Lorsque vous avez résolu tous les problèmes de conception et testé votre modèle, vous êtes prêt pour le déploiement. À ce stade, vous pouvez définir la méthode recommandée pour répondre aux requêtes sur le modèle. Voulez-vous que les utilisateurs aient accès au cache, ou utilisent toujours uniquement la source de données relationnelle ?  
  
 Si vous déployez le modèle en *mode hybride*, le cache reste disponible et peut être utilisé pour les requêtes. Un mode hybride vous fournit de nombreuses options :  
  
-   Lorsque le cache et la source de données relationnelle sont disponibles, vous pouvez définir la méthode de connexion recommandée par défaut, mais en fin de compte le client contrôle la source utilisée, à l'aide de la propriété de chaîne de connexion DirectQueryMode.  
  
-   Vous pouvez également configurer des partitions du cache de telle façon que la partition principale utilisée pour le mode DirectQuery ne soit jamais traitée et doive toujours faire référence à la source relationnelle. Il existe plusieurs façons d'utiliser des partitions pour optimiser l'expérience de conception de modèle et de rapports. Pour plus d’informations, consultez [Partitions et DirectQuery Mode &#40;tabulaire SSAS&#41;](define-partitions-in-directquery-models-ssas-tabular.md).  
  
-   Une fois le modèle déployé, vous pouvez modifier la méthode de connexion par défaut. Par exemple, vous pouvez utiliser un mode hybride pour le test, et basculer le modèle en mode **DirectQuery uniquement** seulement après avoir testé complètement tous les rapports ou requêtes qui utilisent le modèle. Pour plus d’informations, consultez [Définir ou modifier la méthode de connexion par défaut pour DirectQuery](../set-or-change-the-preferred-connection-method-for-directquery.md).  
  
###  <a name="bkmk_DataSources"></a> Sources de données pour les modèles DirectQuery  
 Dès que vous modifiez l'environnement de conception pour activer le mode DirectQuery, les sources de données pour la base de données de l'espace de travail sont validées pour garantir qu'elles proviennent d'une seule source de données SQL Server. Les données issues d'autres sources, notamment les données copiées-collées, ne sont pas autorisées dans les modèles DirectQuery.  
  
 Si vous avez l'intention d'utiliser le modèle en mode DirectQuery, vous devez vous assurer que toutes les données dont vous avez besoin pour les rapports sont stockées dans la base de données SQL Server spécifiée. Si les données dont vous avez besoin pour la modélisation ne sont pas disponibles dans cette source, envisagez d'utiliser Integration Services ou d'autres outils de stockage des données pour importer les données dans une base de données SQL Server qui sert de source de données DirectQuery.  
  
###  <a name="bkmk_Validation"></a> Restrictions de validation et conception pour le Mode DirectQuery  
 Lorsque vous créez un modèle utilisable en mode DirectQuery, vous devez initialement charger une partie des données dans le cache. Si les données que vous utiliserez par la suite sont trop volumineuses pour tenir en mémoire, vous pouvez utiliser la **aperçu et filtrer** option dans l’Assistant Importation de Table pour sélectionner un sous-ensemble de données, ou écrire un script SQL pour obtenir les données que vous souhaitez.  
  
> [!WARNING]  
>  Étant donné que le mode DirectQuery ne prend pas en charge l'utilisation de colonnes calculées, s'il existe des colonnes que vous souhaitez combiner ou sur lesquelles vous souhaitez exécuter d'autres opérations, vous devez planifier et créer la définition de colonne dans le cadre de votre requête ou script d'importation de données.  
  
 Pour afficher et résoudre les erreurs de validation, ouvrez la **Liste d'erreurs** dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Les erreurs critiques qui empêchent l'utilisation du mode DirectQuery sont affichées sous l'onglet **Erreurs** . Vous devez corriger ces erreurs avant de passer en mode DirectQuery. Les erreurs de validation les plus difficiles à résoudre sont généralement liées aux formules qui ne sont pas prises en charge en mode DirectQuery. Consultez la section [Compatibilité des formules](#bkmk_FormulaCompat), pour obtenir une vue d'ensemble des erreurs liées aux formules et aux colonnes calculées.  
  
 La liste suivante décrit d'autres considérations à garder à l'esprit lorsque vous créez un modèle pour l'accès DirectQuery :  
  
-   Lorsque vous êtes en mode *DirectQuery uniquement* , les résultats d'un rapport peuvent varier selon le contexte de sécurité de l'utilisateur qui affiche les résultats. Vous devez tester les modèles avec des informations d'identification différentes pour garantir que les utilisateurs reçoivent les résultats attendus.  
  
-   Si vous configurez un modèle pour qu'il fonctionne en mode hybride, ce qui permet l'utilisation du cache ou des données SQL Server, tenez compte de la possibilité que les clients qui se connectent à chaque source voient des résultats différents en fonction du mode spécifié dans la chaîne de connexion. Si vous devez vous assurer que les utilisateurs de rapports voient uniquement les données de SQL Server, vous devez effacer le cache ou changer le modèle en DirectQueryOnly.  
  
###  <a name="bkmk_FormulaCompat"></a> Compatibilité des formules pour les modèles DirectQuery  
 Certains modèles peuvent contenir des formules qui ne sont pas prises en charge en mode DirectQuery, et le modèle doit être refondu pour éviter des erreurs de validation. Les restrictions sur les formules qui sont prises en charge en mode DirectQuery sont les suivantes :  
  
-   Les colonnes calculées ne sont prises en charge dans aucun modèle tabulaire qui a le mode DirectQuery activé, même pas les modèles hybrides. Si vous avez besoin de colonnes calculées pour un modèle, envisagez de les convertir en colonnes dérivées à l'aide de Transact-SQL dans votre définition de l'importation.  
  
-   Les modèles DirectQuery prennent en charge l'utilisation de formules DAX pour une utilisation dans des mesures, qui sont converties en opérations basées sur un ensemble par rapport à la banque de données relationnelle. Toutes les mesures que vous créez à l'aide de mesures implicites sont prises en charge.  
  
-   Toutes les fonctions ne sont pas prises en charge. Étant donné qu' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] convertit toutes les formules DAX et définitions de mesure en instructions SQL en interrogeant un modèle DirectQuery, toute formule qui contient des éléments qui ne peuvent pas être convertis en Transact-SQL déclenche des erreurs de validation sur le modèle. Par exemple, les fonctions Time Intelligence ne sont pas prises en charge. Même les fonctions prises en charge peuvent se comporter différemment, comme les fonctions statistiques. Pour obtenir une liste complète des problèmes de compatibilité, consultez [compatibilité des formules en DirectQuery Mode](../dax-formula-compatibility-in-directquery-mode-ssas-2014.md).  
  
-   Certaines formules du modèle peuvent se valider lorsque vous basculez le modèle en mode DirectQuery, mais retournent des résultats différents une fois exécutées sur le cache et la banque de données relationnelle. Cela est dû au fait que les calculs sur le cache utilisent la sémantique du moteur d'analyse en mémoire xVelocity (VertiPaq), qui contient de nombreuses fonctionnalités pour émuler le comportement d'Excel, alors que les requêtes sur des données stockées dans la banque de données relationnelle utilisent obligatoirement la sémantique de SQL Server. Pour obtenir la liste des fonctions DAX qui peuvent retourner des résultats différents lorsque le modèle est déployé en temps réel, consultez [compatibilité des formules en DirectQuery Mode](../dax-formula-compatibility-in-directquery-mode-ssas-2014.md).  
  
###  <a name="bkmk_Connecting"></a> Connexion aux modèles DirectQuery  
 Les clients qui utilisent le langage de requête MDX ne peuvent pas se connecter aux modèles qui utilisent le mode DirectQuery. Par exemple, si vous essayez de créer une requête MDX sur un modèle DirectQuery, vous obtiendrez une erreur indiquant que le cube est introuvable, ou n'a pas été traité. Vous pouvez créer diverses requêtes sur les modèles DirectQuery à l'aide de [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)], de formules DAX ou de requêtes XMLA. Pour plus d'informations sur l'exécution de requêtes ad hoc sur les modèles tabulaires, consultez [Tabular Model Data Access](tabular-model-data-access.md).  
  
 Si vous utilisez un modèle hybride, vous pouvez spécifier si les utilisateurs se connectent au cache ou utilisent les données de DirectQuery en spécifiant la propriété de chaîne de connexion DirectQueryMode.  
  
###  <a name="bkmk_Security"></a> Sécurité en Mode DirectQuery  
 Pendant le processus de création de modèle, vous spécifiez les autorisations utilisées pour récupérer les données source. Il s'agit souvent de vos propres informations d'identification, ou d'un compte utilisé pour le développement. Toutefois, lorsque vous basculez le modèle pour qu'il utilise le mode DirectQuery, le contexte de sécurité est plus complexe :  
  
-   Déterminez si les utilisateurs disposent du niveau d'accès nécessaire aux données de la banque de données relationnelle.  
  
-   Les utilisateurs qui consultent le même modèle ou rapport peuvent voir des données différentes, selon le contexte de sécurité utilisateur.  
  
-   Si le cache des modèles a été conservé, il est sécurisé à l'aide du modèle de sécurité (de rôles) [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Le cache peut contenir des données que le concepteur de modèles est autorisé à consulter contrairement à l'utilisateur. Les concepteurs de modèles et de rapports doivent effacer le cache, ou sécuriser ces données en contrôlant l'accès par le biais de rôles.  
  
-   Un modèle qui répond aux requêtes du cache ne peut pas emprunter l'identité de l'utilisateur actuel lors de la connexion à la source de données. Si vous souhaitez emprunter l'identité de l'utilisateur actuel lors de la connexion à la source de données, vous devez utiliser le mode DirectQuery.  
  
-   Si votre modèle de rapport nécessite la mise en place d'une sécurité, vous avez deux options : utiliser des rôles [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , ou définir des autorisations au niveau des lignes sur la source de données. La sécurité dans la source de données relationnelle est utilisée pour contrôler l'accès aux tables, et la sécurité au niveau des colonnes n'est pas prise en charge. Par conséquent, si les utilisateurs dans une région n'ont pas l'autorisation d'afficher les chiffres des ventes de différentes régions, un rapport qui comprend une mesure en fonction de la table Sales retourne des espaces ou une erreur.  
  
 La propriété de paramètres d'emprunt d'identité spécifie les informations d'identification utilisées lorsque vous vous connectez à un modèle à l'aide de DirectQuery, que ce soit pour un modèle DirectQuery uniquement ou pour un modèle hydride répondant aux requêtes à l'aide de DirectQuery. La propriété possède les valeurs suivantes :  
  
 **Default**  
 Utilise les informations d'identification spécifiées dans l'Assistant Importation pour se connecter à la source de données. Il peut s'agir d'un utilisateur Windows spécifique ou du compte de service.  
  
 `ImpersonateCurrentUser`  
 Utilise les informations d'identification de l'utilisateur actuel pour se connecter à la source de données.  
  
 Pour plus d’informations sur la façon de définir ces propriétés, consultez [les scénarios de déploiement DirectQuery &#40;tabulaire SSAS&#41;](../directquery-deployment-scenarios-ssas-tabular.md).  
  
##  <a name="bkmk_PropertyList"></a> Propriétés DirectQuery  
 Le tableau suivant répertorie les propriétés que vous pouvez définir dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]et dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]pour activer DirectQuery et contrôler la source de données utilisée pour les requêtes sur le modèle.  
  
|Nom de la propriété|Description|  
|-------------------|-----------------|  
|**Propriété DirectQueryMode**|Cette propriété permet d'utiliser le mode DirectQuery dans le concepteur de modèles. Vous devez affecter à cette propriété la valeur `On` pour modifier l'une des autres propriétés DirectQuery.<br /><br /> Pour plus d’informations, consultez [activer le Mode Création DirectQuery &#40;tabulaire SSAS&#41;](enable-directquery-mode-in-ssdt.md).|  
|**Propriété QueryMode**|Cette propriété indique la méthode de requête par défaut pour un modèle DirectQuery. Vous définissez cette propriété dans le concepteur de modèles lorsque vous déployez le modèle, mais vous pouvez la remplacer par la suite. La propriété possède ces valeurs :<br /><br /> **DirectQuery** -ce paramètre spécifie le modèle de toutes les requêtes doivent utiliser la source de données relationnelles uniquement.<br /><br /> **DirectQuery avec In-Memory** : ce paramètre spécifie que, par défaut, il convient de répondre aux requêtes en utilisant la source relationnelle, sauf indication contraire dans la chaîne de connexion du client.<br /><br /> **In-Memory** : ce paramètre spécifie qu’il convient de répondre aux requêtes en utilisant seulement le cache.<br /><br /> **In-Memory avec DirectQuery** : ce paramètre spécifie que par défaut, il convient de répondre aux requêtes en utilisant le cache, sauf indication contraire dans la chaîne de connexion du client.<br /><br /> <br /><br /> Pour plus d’informations, consultez [Définir ou modifier la méthode de connexion par défaut pour DirectQuery](../set-or-change-the-preferred-connection-method-for-directquery.md).|  
|**Propriété DirectQueryMode**|Une fois le modèle déployé, vous pouvez modifier la source de données de requête par défaut pour un modèle DirectQuery, en modifiant cette propriété dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].<br /><br /> Comme la propriété précédente, cette propriété indique la source de données par défaut pour le modèle, et possède les valeurs suivantes :<br /><br /> **InMemory**: Requêtes peuvent utiliser le cache uniquement.<br /><br /> **DirectQuerywithInMemory**: les requêtes utilisent la source de données relationnelle par défaut, sauf indication contraire dans la chaîne de connexion du client.<br /><br /> **InMemorywithDirectQuery**: les requêtes utilisent le cache par défaut, sauf indication contraire dans la chaîne de connexion du client.<br /><br /> (**DirectQuery**: les requêtes utilisent la source de données relationnelle uniquement.<br /><br /> <br /><br /> Pour plus d’informations, consultez [Définir ou modifier la méthode de connexion par défaut pour DirectQuery](../set-or-change-the-preferred-connection-method-for-directquery.md).|  
|**Propriété de paramètres d’emprunt d’identité**|Cette propriété définit les informations d'identification utilisées pour la connexion à la source de données SQL Server au moment de la requête. Vous pouvez définir cette propriété dans le concepteur de modèles, et vous pouvez modifier la valeur ultérieurement, une fois le modèle déployé.<br /><br /> Notez que ces informations d'identification sont utilisées uniquement pour répondre aux requêtes sur la banque de données relationnelle ; elles sont différentes des informations d'identification utilisées pour traiter le cache d'un modèle hybride.<br /><br /> L'emprunt d'identité ne peut pas être utilisé lorsque le modèle est utilisé dans la mémoire uniquement. La paramètre `ImpersonateCurrentUser` n'est pas valide, sauf si le modèle utilise le mode DirectQuery.|  
  
 En outre, si votre modèle inclut des partitions, vous devez choisir une partition à utiliser comme source pour les requêtes en mode DirectQuery. Pour plus d’informations, consultez [Partitions et DirectQuery Mode &#40;tabulaire SSAS&#41;](define-partitions-in-directquery-models-ssas-tabular.md).  
  
##  <a name="bkmk_related_tasks"></a> Tâches et rubriques connexes  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Partitions et Mode DirectQuery &#40;SSAS tabulaire&#41;](define-partitions-in-directquery-models-ssas-tabular.md)|Décrit la manière dont les partitions sont utilisées dans les modèles configurés pour le mode DirectQuery.|  
|[Compatibilité des formules DAX en mode DirectQuery](../dax-formula-compatibility-in-directquery-mode-ssas-2014.md)|Décrit les restrictions et les spécifications de compatibilité applicables aux formules que vous pouvez utiliser dans les modèles configurés pour le mode DirectQuery.|  
|[Activer le Mode Création DirectQuery &#40;SSAS tabulaire&#41;](enable-directquery-mode-in-ssdt.md)|Explique comment vous pouvez modifier l'environnement au moment de la conception afin qu'il prenne en charge l'utilisation du mode DirectQuery|  
|[Modifier la Partition DirectQuery &#40;SSAS tabulaire&#41;](../change-the-directquery-partition-ssas-tabular.md)|Explique comment modifier la partition DirectQuery.|  
|[Définir ou modifier la méthode de connexion par défaut pour DirectQuery](../set-or-change-the-preferred-connection-method-for-directquery.md)|Explique comment définir ou modifier la méthode de connexion pour les modèles configurés pour DirectQuery.|  
|[Scénarios de déploiement DirectQuery &#40;SSAS tabulaire&#41;](../directquery-deployment-scenarios-ssas-tabular.md)|Décrit les scénarios de déploiement de DirectQuery.|  
|[Configurer l’accès en mémoire ou DirectQuery pour une base de données de modèle tabulaire](enable-directquery-mode-in-ssms.md)|Comprendre les configurations DirectQuery|  
|[Effacer les caches Analysis Services](../instances/clear-the-analysis-services-caches.md)|Effacer le cache du modèle tabulaire|  
  
## <a name="see-also"></a>Voir aussi  
 [Partitions &#40;SSAS Tabulaire&#41;](partitions-ssas-tabular.md)   
 [Projets de modèles tabulaires &#40;SSAS Tabulaire&#41;](tabular-model-projects-ssas-tabular.md)   
 [Analyser dans Excel &#40;SSAS Tabulaire&#41;](analyze-in-excel-ssas-tabular.md)  
