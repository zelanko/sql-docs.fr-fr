---
title: Utilisation des indicateurs de performance clés dans Reporting Services | Microsoft Docs
description: Découvrez comment vous pouvez facilement mesurer l’état et les performances à l’aide des indicateurs de performance clés dans SQL Server Reporting Services.
author: maggiesMSFT
ms.author: maggies
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.date: 07/02/2017
ms.openlocfilehash: e661fee4e9b5afe5f78cae444ff8d6574a536bb9
ms.sourcegitcommit: 80701484b8f404316d934ad2a85fd773e26ca30c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93243778"
---
# <a name="working-with-kpis-in-reporting-services"></a>Utilisation des indicateurs de performance clés dans Reporting Services

[!INCLUDE[ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../includes/ssrs-appliesto-pbirs.md)]

Un *indicateur de performance clé (KPI)* est un indice visuel qui représente la progression vers un objectif.  Les Indicateurs de performance clés sont utiles pour les équipes, les responsables et les entreprises pour évaluer rapidement l’état d’avancement par rapport à des objectifs mesurables.
  
En utilisant les indicateurs de performance clés dans SQL Server Reporting Services, vous pouvez facilement visualiser les réponses aux questions suivantes :  
  
- Suis-je en avance ou en retard ?  
  
- Quelle est mon avance ou quel est mon retard ?  
  
- Quels sont les montants minimaux que j’ai effectués ?  

> [!NOTE]
> Les indicateurs de performance clés sont accessibles uniquement dans les éditions Entreprise (Développeur) du portail SSRS.

## <a name="creating-a-dataset"></a>Création d’un dataset

Un indicateur de performance clé utilise uniquement la première ligne de données issue d’un dataset partagé. Assurez-vous que les données que vous souhaitez utiliser se trouvent sur cette première ligne. Pour créer un dataset partagé, vous pouvez utiliser le Générateur de rapports ou SQL Server Data Tools.  
  
> **Remarque**  : Le dataset ne doit pas nécessairement être dans le même dossier que l’indicateur de performance clé.  
  
## <a name="placement-of-kpis"></a>Positionnement des indicateurs de performance clés  
  
Les indicateurs de performance clés peuvent être créés dans n’importe quel dossier sur votre serveur de rapports.  Avant de créer un indicateur de performance clé, vous devez réfléchir au meilleur emplacement pour celui-ci. Vous pouvez le placer dans un dossier visible pour les utilisateurs, qui soit en même temps utile à d’autres rapports et indicateurs de performance clés.  
## <a name="adding-a-kpi"></a>Ajout d’un indicateur de performance clé
  
Après avoir déterminé l’emplacement de votre indicateur de performance clé, accédez à ce dossier et sélectionnez **Nouveau** > **Indicateur de performance clé** dans le menu supérieur.  
  
![Capture d’écran montrant la liste déroulante Nouveau avec l’option Indicateur de performance clé mise en évidence.](../reporting-services/media/rscreatekpi1.png)  
  
L’écran **Nouvel indicateur de performance clé** s’affiche.  
  
![Capture d’écran montrant l’écran Nouvel indicateur de performance clé.](../reporting-services/media/rscreatekpi2.png)  
  
Vous pouvez assigner des valeurs statiques ou utiliser les données issues d’un dataset partagé. Lorsque vous créez un indicateur de performance clé, il est rempli avec une série aléatoire de données manuelles.  
  
| Champ | Description |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| Format de valeur | Permet de modifier le format de la valeur affichée. |
| Valeur | La valeur à afficher pour l’indicateur de performance clé. |
| Objectif | Utilisé en comparaison à une valeur numérique et présenté sous forme de différence de pourcentage. |
| Statut | Valeur numérique utilisée pour déterminer la couleur de vignette de l’indicateur de performance clé. Les valeurs valides sont 1 (vert), 0 (orange) et -1 (rouge). |
| Ensemble de tendances | Valeurs numériques séparées par des virgules utilisées pour la visualisation de graphique. Ceci peut également être défini sur une colonne d’un dataset avec des valeurs qui représentent la tendance. |
| Contenu connexe | Possibilité de définir un lien d’extraction. Ce lien peut être un rapport mobile publié sur le portail ou une URL personnalisée. |
  
> **Avertissement** : bien que vous pouvez utiliser la valeur texte pour le champ **État** au moment de la conception, vous devez utiliser la valeur numérique en cas d’actualisation d’un dataset. Si vous actualisez un dataset avec la valeur texte, au lieu de la valeur numérique, cela peut endommager les indicateurs de performance clés sur votre serveur.  
>
> **Remarque**  : La valeur des champs **Valeur** , **Objectif** et **État** peut être choisie seulement dans la première ligne du résultat d’un dataset. Toutefois, le champ **Ensemble de tendances** peut choisir la colonne qui reflète la tendance.  
  
Vous pouvez procéder comme suit pour utiliser les données d’un jeu de données partagé.
  
1. Modifiez la liste déroulante des champs de **Manuellement** ou **Ne pas définir** à **Champ de dataset**.  
  
    ![Capture d’écran montrant l’option Valeur définie sur Champ de jeu de données et l’option Sélectionner un champ de jeu de données définie sur Non défini.](../reporting-services/media/rscreatekpi3.png)  
  
2. Sélectionnez les **points de suspension (...)** dans la zone de données. L’écran **Choisir un dataset** s’affiche.  
  
    ![Capture d’écran de la section Choisir un jeu de données avec l’option Finance_KPI sélectionnée.](../reporting-services/media/rscreatekpi4.png)  
  
3. Sélectionnez le dataset qui contient les données que vous souhaitez afficher.  
  
4. Choisissez le champ que vous souhaitez utiliser. Sélectionnez **OK**.  
  
    ![Capture d’écran montrant la section Choisir un champ dans la section Finance_KPI avec l’option Sum_Amount sélectionnée.](../reporting-services/media/rscreatekpi5.png)  
  
5. Modifiez **Format de la valeur** pour correspondre au format de la valeur. Dans cet exemple, la valeur est une devise.  
  
    ![Capture d’écran de l’aperçu de l’indicateur de performance clé montrant l’option Format de la valeur définie sur Devise.](../reporting-services/media/rscreatekpi6.png)  
  
6. Sélectionnez **Appliquer**.  
  
    ![Capture d’écran des indicateurs de performance clés montrant que les jeux de données ont deux éléments.](../reporting-services/media/rscreatekpi7.png)

## <a name="configuring-related-content"></a>Configuration du contenu associé

Lorsque vous choisissez **Rapport mobile** , vous pouvez choisir la destination dans une boîte de dialogue.

   ![Capture d’écran montrant l’option Contenu associé définie sur Rapport mobile et l’option Choisir un rapport mobile définie sur Non défini.](media/rscreatekpi-related-content-mobile-report.png)

Quand vous cliquez maintenant sur l’indicateur de performance clé dans le portail, une miniature du rapport mobile s’affiche sous la liste déroulante du contenu associé. Cliquez sur cette miniature pour accéder directement à ce rapport.

Vous pouvez également spécifier une URL personnalisée. Cette tâche peut être : un site web, un site SharePoint, une URL vers un rapport SSRS (ce qui vous permet de transmettre des paramètres codés en dur).

![Capture d’écran montrant l’option Contenu associé définie sur URL personnalisée et l’option Entrer une URL définie sur http://.](media/rscreatekpi-related-content-custom-url.png)

Lorsque vous cliquez à présent sur l’indicateur de performance clé, l’URL s’affiche sous le contenu associé.

Il n’est possible d’ajouter qu’un seul rapport mobile ou une seule URL personnalisée.
  
## <a name="removing-a-kpi"></a>Suppression d’un indicateur de performance clé  
  
Pour supprimer un indicateur de performance clé, vous pouvez suivre les étapes suivantes.
  
1. Sélectionnez les **points de suspension (...)** de l’indicateur de performance clé à supprimer. Sélectionnez **Gérer**.  
  
    ![Capture d’écran de l’option des points de suspension pour un indicateur de performance clé sélectionnée et l’option Gérer mise en évidence.](../reporting-services/media/rsremovekpi1.png)  
  
2. Sélectionnez **Supprimer**. Sélectionnez **Supprimer** à nouveau dans la boîte de dialogue de confirmation.  
  
    ![Capture d’écran de l’option Supprimer.](../reporting-services/media/rsremovekpi2.png)  
  
## <a name="refreshing-a-kpi"></a>Actualisation d’un indicateur de performance clé  
  
Pour actualiser l’indicateur de performance clé, vous devez configurer une mise en cache pour le dataset partagé. Pour plus d’informations sur les plans d’actualisation du cache, consultez [Utiliser des datasets partagés](../reporting-services/work-with-shared-datasets-web-portal.md).  
  
## <a name="next-steps"></a>Étapes suivantes
  
[Portail Web](../reporting-services/web-portal-ssrs-native-mode.md)  
[Utiliser des datasets partagés](../reporting-services/work-with-shared-datasets-web-portal.md)

D’autres questions ? [Essayez de poser une question dans le forum Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231)
