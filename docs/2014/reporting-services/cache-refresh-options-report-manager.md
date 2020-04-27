---
title: Options d’actualisation du cache (Gestionnaire de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 227da40c-6bd2-48ec-aa9c-50ce6c1ca3a6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6ae1ee11edd51153585e9a6738bbfbd59af8974f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66109919"
---
# <a name="cache-refresh-options-report-manager"></a>Options d’actualisation du cache (Gestionnaire de rapports)
  La page Options d'actualisation du cache permet de créer des planifications pour précharger des copies temporaires des données d'un rapport ou d'un dataset partagé dans le cache. Un plan d'actualisation inclut une planification et la possibilité de spécifier ou de remplacer des valeurs pour les paramètres. Dans le cas d'un dataset partagé, vous ne pouvez pas remplacer les valeurs des paramètres marqués en lecture seule. Vous pouvez créer et utiliser plusieurs plans d'actualisation dans la page des options d'actualisation.  
  
 Les attributions de rôle par défaut qui vous permettent d'ajouter, de supprimer, de modifier et d'afficher des datasets partagés et des rapports connexes pour des plans d'actualisation du cache sont les suivantes : Gestionnaire de contenu, Mes Rapports et Serveur de publication.  
  
> [!NOTE]  
>  Cette fonctionnalité n'est pas disponible dans toutes les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour obtenir une liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], consultez [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="to-open-the-cache-refresh-plan-properties-page-for-a-report-or-shared-dataset"></a>Pour ouvrir la page des propriétés du plan d'actualisation du cache pour un rapport ou un dataset partagé  
  
1.  Ouvrez le Gestionnaire de rapports et accédez au rapport ou au dataset partagé pour lequel vous voulez configurer les propriétés du plan d'actualisation du cache.  
  
2.  Pointez sur le rapport ou le dataset partagé, puis cliquez sur la flèche déroulante.  
  
3.  Dans la liste déroulante, cliquez sur **Gérer**. La page **Propriétés générales** s’ouvre.  
  
4.  Cliquez sur l'onglet **Plan d'actualisation du cache** .  
  
5.  Pour créer un plan de cache, cliquez sur **Nouveau plan d'actualisation du cache**.  
  
    > [!NOTE]  
    >  Vous devez activer et démarrer le service SQL Server Agent pour créer un plan d'actualisation du cache.  
  
6.  Pour créer une copie d'un plan d'actualisation du cache puis la personnaliser, cliquez sur **Créer à partir d'un document existant**.  
  
## <a name="cache-refresh-options"></a>Options d'actualisation du cache  
 **Supprimer**  
 Supprime tous les plans d'actualisation actuellement sélectionnés.  
  
 **Créer à partir d'un document existant**  
 Cette option est activée lorsqu'un seul plan d'actualisation du cache est sélectionné. Cette option crée un nouveau plan d'actualisation copié à partir du plan d'origine. La page du plan d'actualisation du cache qui s'ouvre contient les détails du plan sélectionné. Vous pouvez alors modifier les options du plan d'actualisation et enregistrer ce dernier en utilisant une nouvelle description.  
  
 **Nouveau plan d'actualisation du cache**  
 Cliquez pour créer un plan d'actualisation à utiliser dans les options d'actualisation du cache actuelles.  
  
 **Modifier**  
 Sélectionnez cette option pour modifier le plan d'actualisation actuel.  
  
## <a name="cache-refresh-plan-options"></a>Options du plan d'actualisation du cache  
 **Description**  
 Spécifiez une description pour le plan d'actualisation du cache.  
  
 **Planification spécifique aux éléments**  
 Sélectionnez cette option pour créer une planification qui est utilisée uniquement par cet élément.  
  
 **Configurer**  
 Cliquez pour ouvrir la page Planification qui permet de spécifier les informations de fréquence.  
  
 Pour plus d’informations, consultez [nouvelle planification : modifier la page de planification &#40;Gestionnaire de rapports&#41;](../../2014/reporting-services/new-schedule-edit-schedule-page-report-manager.md).  
  
 **Planification partagée**  
 Sélectionnez cette option pour sélectionner une planification existante.  
  
 Pour plus d’informations, consultez [Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md).  
  
 **@\<***Paramètre***>**  
 Spécifiez une combinaison de valeurs de paramètre. Cette section apparaît uniquement si le rapport ou le dataset actuel comporte des paramètres.  
  
 Consultez [Spécification des paramètres](#Parameters) dans la section suivante.  
  
 **Utiliser la valeur par défaut**  
 Sélectionnez cette option afin d'utiliser la valeur par défaut prédéfinie pour ce paramètre.  
  
##  <a name="specifying-parameters"></a><a name="Parameters"></a>Spécification des paramètres  
 Pour que vous puissiez créer un plan d'actualisation du cache, chaque paramètre de dataset partagé ou de rapport doit comporter une valeur. Si aucune valeur par défaut n'est spécifiée dans la définition de l'élément de rapport ou de dataset partagé, vous devez indiquer une valeur. S'il existe une valeur par défaut, il est inutile d'en fournir une ici. Si vous spécifiez une valeur, elle remplace la valeur par défaut.  
  
 Pour spécifier plusieurs combinaisons de valeurs de paramètre, vous devez créer un plan d'actualisation du cache distinct pour chaque combinaison.  
  
 Les modifications, suppressions et ajouts apportés aux paramètres d'un rapport ou d'un dataset partagé peuvent avoir une incidence sur le plan d'actualisation du cache. Si vous ajoutez un paramètre avec une valeur par défaut pour un rapport, supprimez un paramètre, ou modifiez le type de données ou l'option Lecture seule d'un paramètre de dataset partagé, les modifications prennent effet lors du traitement suivant du plan d'actualisation du cache.  
  
### <a name="shared-dataset-parameters"></a>Paramètres de dataset partagé  
 Pour un dataset partagé, les informations suivantes sont dérivées de la définition du dataset partagé :  
  
-   **Nom** Spécifie le nom du paramètre de requête.  
  
-   **Type** Spécifie le type de données du paramètre de requête. Étant donné que ce type de données est inconnu tant que le fournisseur de données n'a pas traité la requête de dataset, la validation du type de données ne peut pas avoir lieu avant le traitement du dataset partagé.  
  
-   **Nullable** Spécifie si NULL est une valeur valide.  
  
-   **Lecture seule** Spécifie si ce paramètre est marqué en lecture seule dans la définition du dataset partagé. Les paramètres en lecture seule n'apparaissent pas dans la liste des paramètres des options d'actualisation du cache et doivent être dotés d'une valeur par défaut spécifiée dans la définition du dataset partagé.  
  
-   **Valeurs par défaut** Il s'agit des valeurs par défaut qui ont été spécifiées dans la définition du dataset partagé. Les paramètres de requête peuvent être à valeurs multiples. Pour remplacer les valeurs par défaut, tapez de nouvelles valeurs dans les zones de message des champs de texte.  
  
 Si la définition du dataset partagé spécifie l'option **Omettre de la requête** pour un paramètre, il est inutile de fournir une valeur par défaut. Cet indicateur signale que le paramètre de dataset n'est pas utilisé dans la requête. Par exemple, le paramètre apparaît dans la définition du dataset partagé, car il s'agit d'un paramètre de rapport employé uniquement dans le filtre de dataset.  
  
 Pour afficher ou modifier les options des paramètres de dataset, vous devez modifier la définition du dataset partagé. Pour plus d’informations, consultez [Gérer des datasets partagés](report-data/manage-shared-datasets.md).  
  
### <a name="report-parameters"></a>Paramètres de rapport  
 Dans le cas d'un rapport, chaque valeur de paramètre doit être valide pour que vous puissiez créer un plan d'actualisation du cache. Vous devez taper ou sélectionner une valeur par défaut pour chaque paramètre de rapport. La valeur que vous définissez remplace la valeur par défaut définie pour le paramètre de rapport sur le serveur de rapports.  
  
 Les paramètres doivent respecter les critères requis spécifiés dans les propriétés de paramètre sur le serveur de rapports. Par exemple, si la propriété AllowBlank a la valeur false pour un paramètre de rapport, une chaîne vide n’est pas une valeur valide.  
  
 Pour afficher ou modifier les options des paramètres de rapport, vous devez modifier les paramètres de rapport dans le rapport, ou indépendamment, sur le serveur de rapports. Pour plus d’informations, consultez [concept des paramètres de rapport &#40;générateur de rapports et&#41;SSRS ](report-design/report-parameters-concepts-report-builder-and-ssrs.md).  
  
## <a name="conditions-that-cause-a-cache-refresh-plan-to-be-inactive"></a>Conditions provoquant l'inactivité d'un plan d'actualisation du cache  
 Le plan d'actualisation du cache d'un rapport ou d'un dataset partagé peut devenir inactif dans les conditions suivantes.  
  
-   L'option de cache du rapport ou du dataset partagé est désactivée.  
  
-   Les valeurs de paramètre obligatoires ne sont pas définies, ne sont pas valides ou sont manquantes. Toutes les requêtes pour un rapport doivent être valides afin de permettre le traitement du rapport. Lorsqu'un rapport comporte des sous-rapports, toutes les requêtes de dataset, y compris les datasets du sous-rapport, sont traitées en premier. Si un dataset ne peut pas être traité correctement, l'exécution du rapport est impossible.  
  
## <a name="conditions-that-cause-a-cache-refresh-plan-to-be-reactivated"></a>Conditions provoquant la réactivation d'un plan d'actualisation du cache  
 Lorsqu'un plan est devenu inactif, effectuez l'une des opérations suivantes pour déclencher l'évaluation d'un plan d'actualisation du cache :  
  
-   Modifiez une option du plan.  
  
-   Activez la mise en cache d'un dataset partagé ou d'un rapport associé au plan d'actualisation.  
  
-   Désélectionnez ou sélectionnez l'option Lecture seule pour un paramètre de requête de dataset associé au plan d'actualisation, puis enregistrez la nouvelle définition sur le serveur de rapports.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches au niveau élément](security/tasks-and-permissions-item-level-tasks.md)   
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Aide (F1) Gestionnaire de rapports](../../2014/reporting-services/report-manager-f1-help.md)   
 [Mise en cache de rapports &#40;SSRS&#41;](report-server/caching-reports-ssrs.md)   
 [Gérer des datasets partagés](report-data/manage-shared-datasets.md)  
  
  
