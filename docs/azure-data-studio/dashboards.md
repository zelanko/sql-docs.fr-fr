---
title: Accéder rapidement aux insights et des tâches courantes dans Azure Data Studio | Microsoft Docs
description: En savoir plus sur l’affichage des widgets dans Azure Data Studio.
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: b163d110353d07811f0feb991772c90053651659
ms.sourcegitcommit: 35e4c71bfbf2c330a9688f95de784ce9ca5d7547
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49356192"
---
# <a name="dashboards-in-includename-sosincludesname-sos-shortmd"></a>Tableaux de bord dans [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Pour afficher un tableau de bord, un clic droit un serveur ou une base de données et sélectionner **gérer**.

![Exemple de tableau de bord](media/dashboards/sample-dashboard.png)

**Propriétés du serveur** contient les propriétés du serveur, y compris les versions, Édition, nom de l’ordinateur et du système d’exploitation.

**Tâches** contient commons des tâches telles que la restauration et la nouvelle requête.

**Rechercher des bases de données** rechercher facilement des bases de données existantes stockées sur le serveur, y compris les tables.

**État de la sauvegarde** facilement rechercher l’état de sauvegarde pour les bases de données existantes.

## <a name="configuring-insight-widgets"></a>Configuration des Widgets d’analyse
Il est vivement recommandé de suivre le didacticiel pour configurer votre tableau de bord, ce qui se trouve [ici](tutorial-build-custom-insight-sql-server.md).

En outre, veillez à consulter le [savoir-faire sur la configuration des widgets d’analyse]().

Une fois ce didacticiel, poursuivez votre lecture pour plus d’informations sur les widgets spécifiques qui ne sont pas traitées dans ce didacticiel.

## <a name="insight-detail"></a>Détail d’Insight
La fenêtre Détails de Insight mobile fournit des informations détaillées pour un widget insight connexes. 
- Un widget d’Insight restitue une vue de résumé at-a-glance avec count, ligne, etc. de graphique. 
- La fenêtre Détails de Insight mobile fournit des détails « Explorer », répertoriant les données plus précises pour chaque élément répertorié dans le widget un aperçu de haut niveau. 
  - Le contenu du menu volant détails est défini avec une requête SQL distincte pour les requêtes du widget principal. 

Il n’est pas nécessaire de jeu pour une requête de détails Insight, mais la disposition est standard.
- La moitié supérieure de la vue est toujours une vue « summary » 2 colonnes. Les colonnes à utiliser sont définies par les propriétés « label » et « valeur » de la configuration JSON
- En cliquant sur une ligne dans la table de résumé, le bas la moitié du Lanceur répertorie l’ensemble des informations de colonne pour cette ligne.

### <a name="insight-detail-configuration-in-packagejson"></a>Configuration de détail Insight dans le fichier package.json

Exemple de configuration de menu volant Insight détails
```json
"details": {
    "queryFile": "./relative_path_to_sqlfile_from_package_json_file.sql",
    "label": {
        "icon": "database",
        "column": "first_column_name_for_summary_list_view",
        "state": [
            {
                "condition": {
                    "if": "equals",
                    "equals": "0"
                },
                "color": "red"
            },
            {
                "condition": {
                    "if": "equals",
                    "equals": "1"
                },
                "color": "orange"
            },
            {
                "condition": {
                    "if": "equals",
                    "equals": "2"
                },
                "color": "green"
            }
        ]
    },
    "value": "second_column_and_condition_check_value_column_for_summary_list_view",
```
|propriété|Type|valeur|Valeur par défaut|description|comment|
|:---|:---|:---|:---|:---|:---|
|détails|objet JSON|||propriété obligatoire à définir des définitions de détail insight dans sa structure||
|queryFile|chaîne|||le chemin d’accès du fichier de requête sql insight en détail et le nom de fichier relatif à l’emplacement de package.json||
|Étiquette|objet JSON|||propriété obligatoire pour définir chaque élément de ligne dans la vue liste récapitulative|dans les futures le nom de cette propriété à modifier, comme « summaryList »|
|Icône|chaîne|||indiquer le nom de l’icône à consulter pour chaque élément de la vue liste récapitulative.|liste (tbd) des icônes pris en charge est documentée|
|column|chaîne|||indiquer le nom de la première colonne dans la vue liste récapitulative du jeu de résultats de requête|dans les futures le nom de cette propriété devient plus intuitif nom|
|valeur|chaîne|||indiquer le nom de la deuxième colonne dans la vue liste récapitulative du jeu de résultats de requête. La valeur de cette colonne est utilisée pour vérifier les conditions et définir la couleur de point de couleur du chaque liste récapitulative afficher les éléments|dans les futures le nom de cette propriété change pour quelque chose de plus intuitive|
|condition|objet JSON|||définit la vérification de condition pour la valeur de colonne et de déterminer la couleur de chaque élément de la vue liste récapitulative||
|if|chaîne|toujours, equals, notEquals, greaterThan, lessThan, greaterThanOrEqauls, lessThanOrEquals||opérateur de vérification de condition|dans les futures le nom de propriété change à l’opérateur|
|equals|chaîne|||valeur de vérification de condition|dans les futures ce nom de propriété changera à 'value'|

## <a name="insight-actions"></a>Actions d’Insight
Avec un widget d’insight et les détails de l’analyse, vous pouvez facilement y d’un plan d’action pour atténuer un problème ou gérer. Par exemple, vous serez considérer l’exécution de DBCC CHECKDB, lire des journaux d’erreurs ou restaurer la base de données lors de la base de données est en attente de récupération. Ou il peut être une des actions que vous souhaitez effectuer.

À l’aide de [!INCLUDE[name-sos](../includes/name-sos-short.md)]de configuration des Actions d’Insight, vous pouvez mapper un actions intégrées, telles que les restaurer, ou apportez votre propre action définie avec un script sql.

> Configuration des actions personnalisées à l’aide du script sql est en cours de développement et n’est pas disponible dans la version préliminaire privée encore.

## <a name="sample-insight-action-definition"></a>Exemple de définition d’Action d’analyse

```"actions"{}``` définit une action insight. Action peut être définie sur une étendue spécifique tel que ```"server"```, ```"database"``` et ainsi de suite et [!INCLUDE[name-sos](../includes/name-sos-short.md)] transmet les informations de contexte de connexion actuelle à l’action. 

Par exemple, lorsque l’action de restauration est lancée pour la base de données WideWorldImporters, ```"database": "${Database}"``` définition indique qu’il faut pour passer ```Database``` valeur de colonne dans les résultats de votre requête à l’action de restauration. Action de restauration démarre ensuite la base de données. ```"types"``` est un tableau json et plusieurs actions peuvent être répertoriées dans le tableau. Il devient en fait un menu contextuel sur la boîte de dialogue Détails de l’information que l’utilisateur pouvez cliquer sur et effectuer l’action. 

> [!INCLUDE[name-sos](../includes/name-sos-short.md)] version préliminaire 0.17.1 a activé « sauvegarde », « restore », « nouvelle requête » et « nouveau-base de données » en tant que types d’action.

```json
"details": {
    "queryFile": "./sql/database_state_detail.sql",
    "label": {...},
    "value": "state",
    "actions": {
        "database": "${Database}",
        "types": ["restore"]
    }
}
```
