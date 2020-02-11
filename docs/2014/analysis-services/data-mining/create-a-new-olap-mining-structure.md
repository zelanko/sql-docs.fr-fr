---
title: Créer une structure d’exploration de données OLAP | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], OLAP
- mining structures [Analysis Services], creating
- OLAP [Analysis Services], mining models
ms.assetid: 368f4273-a016-4748-bcb6-505a3e745af3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 62f8fc247986609e3822168bff5aace34f3d1aa9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66085457"
---
# <a name="create-a-new-olap-mining-structure"></a>Créer une structure d’exploration de données OLAP
  Vous pouvez utiliser l’Assistant Exploration de données [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans pour créer une structure d’exploration de données qui utilise les données d’un modèle multidimensionnel. Les modèles d'exploration de données basés sur des cubes OLAP peuvent utiliser la colonne et les valeurs des tables de faits, les dimensions et les groupes de mesures comme attributs pour l'analyse.  
  
### <a name="to-create-a-new-olap-mining-structure"></a>Pour créer une structure d'exploration de données OLAP  
  
1.  Dans l’Explorateur de solutions de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], cliquez avec le bouton droit sur le dossier **Structures d’exploration de données** dans un projet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , puis cliquez sur **Nouvelle structure d’exploration de données** pour ouvrir l’Assistant Exploration de données.  
  
2.  Dans la page **Assistant Exploration de données** , cliquez sur **Suivant**.  
  
3.  Dans la page **Sélectionner la méthode de définition** , sélectionnez **À partir d’un cube existant**, puis cliquez sur **Suivant**.  
  
     Si vous obtenez une erreur avec le message Impossible d’extraire une liste d’algorithmes d’exploration de données pris en charge, ouvrez la boîte de dialogue **Propriétés du projet** et vérifiez que vous avez spécifié le nom d’une instance Analysis Services qui prend en charge les modèles multidimensionnels. Vous ne pouvez pas créer de modèles d'exploration de données sur une instance d' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui prend en charge la modélisation tabulaire.  
  
4.  Dans la page **Créer la structure d’exploration de données** , décidez si vous voulez créer une structure d’exploration de données seulement ou une structure d’exploration de données plus un modèle d’exploration de données associé. En général il est plus facile de créer un modèle d'exploration de données en même temps, afin d'être invité à inclure les colonnes nécessaires.  
  
     Si vous envisagez de créer un modèle d’exploration de données, sélectionnez l’algorithme d’exploration de données à utiliser, puis cliquez sur **Suivant**. Pour plus d’informations sur la façon de choisir un algorithme, consultez [Algorithmes d’exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining-algorithms-analysis-services-data-mining.md).  
  
5.  Dans la page **Sélectionner la dimension de cube source** , sous **Sélectionnez une dimension du cube source**, recherchez la dimension qui contient la majorité de vos données de cas.  
  
     Par exemple, si vous essayez d’identifier les regroupements de client, vous pouvez sélectionner la dimension Customer ; si vous essayez d’analyser les achats entre les transactions, vous pouvez sélectionner la dimension Internet Sales Order Details. Vous n'êtes pas limité à utiliser uniquement les données de cette dimension, mais elle doit contenir des attributs importants à utiliser dans l'analyse.  
  
     Cliquez sur **Suivant**.  
  
6.  Dans la page **Sélectionner la clé de cas** , sous **Attributs**, sélectionnez l’attribut qui doit correspondre à la clé de la structure d’exploration de données, puis cliquez sur **Suivant**.  
  
     Généralement l'attribut que vous utilisez comme clé de la structure d'exploration de données est également une clé de la dimension et sera pré-sélectionné.  
  
7.  Dans la page **Sélectionner les colonnes de niveau de cas** , sous **Attributs et mesures associés**, sélectionnez les attributs et les mesures qui contiennent des valeurs que vous souhaitez ajouter à la structure d’exploration de données en tant que données de cas. Cliquez sur **Suivant**.  
  
8.  Dans la page **Spécifier l’utilisation des colonnes du modèle d’exploration de données** , sous **Structure du modèle d’exploration de données**, définissez d’abord la colonne prédictible, puis choisissez ensuite les colonnes à utiliser comme entrées.  
  
    -   Activez la case à cocher dans la colonne la plus à gauche pour inclure les données de la structure d'exploration de données. Vous pouvez inclure des colonnes dans la structure que vous utiliserez pour référence, mais ne pas les utiliser pour l'analyse.  
  
    -   Cochez la case dans la colonne **Entrée** pour utiliser l’attribut comme variable dans l’analyse.  
  
    -   Cochez la case dans la colonne **Prédire** uniquement pour les attributs prédictibles.  
  
     Notez que les colonnes que vous avez désignées comme clés ne peuvent pas être utilisées pour l'entrée ou la prédiction.  
  
     Cliquez sur **Suivant**.  
  
9. Dans la page **Spécifier l’utilisation des colonnes du modèle d’exploration de données** , vous pouvez également ajouter et supprimer des tables imbriquées à la structure d’exploration de données, en utilisant **Ajouter des tables imbriquées** et **Tables imbriquées**.  
  
     Dans un modèle d'exploration de données OLAP, une table imbriquée est un autre jeu de données du cube qui a une relation un-à-plusieurs avec la dimension qui représente les attributs de cas. Par conséquent, lorsque la boîte de dialogue s'ouvre, elle pré-sélectionne les groupes de mesures qui sont déjà liés à la dimension sélectionnée comme table de cas. À ce stade, vous devez choisir une autre dimension qui contient des informations supplémentaires utiles pour l'analyse.  
  
     Par exemple, si vous analysez les clients, vous devez utiliser la dimension [Customer] comme table de cas. Pour la table imbriquée, vous pouvez ajouter les raisons des clients citées en effectuant un achat, qui sont incluses dans la dimension [Sales Reason].  
  
     Si vous ajoutez des données imbriquées, vous devez spécifier deux colonnes supplémentaires :  
  
    -   La clé de la table imbriquée : elle doit être pré-sélectionnée dans la page **Sélectionner la clé de la table imbriquée**.  
  
    -   Le ou les attributs à utiliser pour l’analyse : la page **Sélectionner les colonnes de la table imbriquée**fournit une liste de mesures et d’attributs de la table imbriquée sélectionnée.  
  
        -   Pour chaque attribut que vous incluez dans le modèle, activez la case à cocher dans la colonne gauche.  
  
        -   Si vous souhaitez utiliser l’attribut pour l’analyse uniquement, sélectionnez **Entrée**.  
  
        -   Si vous souhaitez inclure la colonne dans l’un des attributs prédictibles du modèle, sélectionnez **Prédire**.  
  
        -   Tout élément inclus dans la structure mais non spécifié comme entrée ou un attribut prédictible est ajouté à la structure avec l'indicateur `Ignore` ; cela signifie que les données sont traitées lorsque vous générez le modèle, mais ne sont pas utilisées dans l'analyse, et sont disponibles uniquement pour l'extraction. Cela peut être pratique si vous souhaitez inclure des détails tels que des noms de clients, mais que vous ne souhaitez pas les utiliser dans l’analyse.  
  
     Cliquez sur **Terminer** pour fermer la partie de l’Assistant qui fonctionne avec les tables imbriquées. Vous pouvez répéter le processus pour ajouter plusieurs colonnes imbriquées.  
  
10. Dans la page **Spécifier le type de contenu et de données des colonnes** , sous **Structure du modèle d’exploration de données**, définissez le type de contenu et le type de données de chaque colonne.  
  
    > [!NOTE]  
    >  Les modèles d’exploration de données OLAP ne permettent pas d’utiliser la fonction de **détection** pour déterminer automatiquement si une colonne contient des données continues ou discrètes.  
  
     Cliquez sur **Suivant**.  
  
11. Dans la page **Découper le cube source** , vous pouvez filtrer les données utilisées pour créer la structure d’exploration de données.  
  
     Le découpage du cube vous permet de limiter les données utilisées pour générer le modèle. Par exemple, vous pouvez générer des modèles distincts pour chaque zone en découpant la hiérarchie Geography et  
  
    -   **Dimension**: choisissez une dimension associée dans la liste déroulante.  
  
    -   **Hiérarchie**: sélectionnez le niveau de la hiérarchie de dimension auquel vous souhaitez appliquer le filtre. Par exemple, si vous découpez la dimension [Geography], vous devez choisir un niveau de hiérarchie tel que [Region Country Name].  
  
    -   **Opérateur**: choisissez un opérateur dans la liste.  
  
    -   **Expression de filtre**: tapez une valeur ou une expression à utiliser comme condition de filtre, ou utilisez la liste déroulante pour sélectionner une valeur dans la liste des membres au niveau spécifié de la hiérarchie.  
  
         Par exemple, si vous avez sélectionné [Geography] comme dimension et [Region Country Name] comme niveau de la hiérarchie, la liste déroulante contient tous les pays valides que vous pouvez utiliser comme condition de filtre. Vous pouvez effectuer plusieurs sélections. Par conséquent, les données de la structure d'exploration de données seront limitées aux données du cube de ces régions géographiques.  
  
    -   **Paramètres**: ignorez cette case à cocher. Cette boîte de dialogue prend en charge plusieurs scénarios de filtrage du cube et cette option n'est pas appropriée pour générer une structure d'exploration de données.  
  
     Cliquez sur **Suivant**.  
  
12. Dans la page **Fractionner les données en jeux d’apprentissage et jeux de test** , spécifiez un pourcentage des données de la structure d’exploration à réserver pour les tests ou spécifiez le nombre maximal de scénarios de test. Cliquez sur **Suivant**.  
  
     Si vous spécifiez les deux valeurs, les limites sont associées pour que la plus basse soit utilisée.  
  
13. Dans la page **Fin de l’Assistant** , entrez le nom de la nouvelle structure d’exploration de données OLAP et le modèle d’exploration de données initial.  
  
14. Cliquez sur **Terminer**.  
  
15. Dans la page **Fin de l’Assistant** , vous pouvez également créer une dimension du modèle d’exploration de données et/ou un cube en utilisant une dimension du modèle d’exploration de données. Ces options sont prises en charge uniquement pour les modèles créés à l'aide des algorithmes suivants :  
  
    -   Algorithme de gestion de clusters Microsoft  
  
    -   Algorithme MDT (Microsoft Decision Trees)  
  
    -   Algorithme MAR (Microsoft Association Rules)  
  
     **Créer une dimension de modèle d’exploration de données**: activez cette case à cocher et fournissez un nom de type pour la dimension du modèle d’exploration de données. Lorsque vous utilisez cette option, une nouvelle dimension est créée dans le cube d'origine utilisé pour créer la structure d'exploration de données. Vous pouvez utiliser cette dimension pour extraire et réaliser une analyse ultérieure. Étant donné que la dimension se trouve dans le cube, la dimension est automatiquement mappée à la dimension de données de cas.  
  
     **Créer un cube à l’aide**de la dimension du modèle d’exploration de données : activez cette case à cocher et fournissez un nom pour le nouveau cube. Lorsque vous utilisez cette option, un cube est créé. Il contient les dimensions existantes qui ont été utilisées pour générer la structure, et la nouvelle dimension d'exploration de données qui contient les résultats du modèle.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de la structure d'exploration de données et procédures](mining-structure-tasks-and-how-tos.md)  
  
  
