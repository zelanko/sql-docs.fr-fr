---
title: Ajout et modification des sources de données à l’aide de la configuration ( Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], adding
- editing data sources [ODBC], ODBC driver for Oracle
- adding data sources [ODBC], ODBC driver for Oracle
- data sources [ODBC], changing
- data sources [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], adding data sources
ms.assetid: 54b2d61d-6ce5-45af-a776-e03180470ecf
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ae76abc902e4687e5d9891871d7d5d60598b3abc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81281409"
---
# <a name="adding-and-modifying-data-sources-using-setup"></a>Ajout et modification de sources de données via la configuration
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Une source de données identifie un chemin vers les données qui peuvent inclure une bibliothèque réseau, un serveur, une base de données et d’autres attributs - dans ce cas, la source de données est le chemin vers une base de données Oracle. Pour se connecter à une source de données, le Gestionnaire de pilote vérifie le registre Windows pour des informations de connexion spécifiques.  
  
 L’entrée de registre créée par l’administrateur de source de données ODBC est utilisée par le gestionnaire de conducteur ODBC et les chauffeurs ODBC. Cette entrée contient des informations sur chaque source de données et son pilote associé. Avant de pouvoir vous connecter à une source de données, ses informations de connexion doivent être ajoutées au registre.  
  
 Pour ajouter et configurer des sources de données, utilisez [l’administrateur de source de données ODBC](../../odbc/admin/odbc-data-source-administrator.md). L’administrateur ODBC met à jour vos informations de connexion source de données. Lorsque vous ajoutez des sources de données, l’administrateur de l’ODBC met à jour les informations du registre pour vous.  
  
### <a name="to-add-a-data-source-for-windows"></a>Pour ajouter une source de données pour Windows  
  
1.  Ouvrez l’administrateur de source de données ODBC.  
  
2.  Dans la boîte de dialogue de l’administrateur de source de données ODBC, cliquez sur Ajouter. La boîte de dialogue Creat New Data Source apparaît.  
  
3.  Sélectionnez Microsoft ODBC pour Oracle, puis cliquez sur Finition. La boîte de dialogue Microsoft ODBC pour Oracle Setup apparaît.  
  
4.  Dans la boîte de noms de source de données, tapez le nom de la source de données à laquelle vous souhaitez accéder. Il peut être n’importe quel nom que vous choisissez.  
  
5.  Dans la boîte de description, tapez la description pour le conducteur. Ce champ optionnel décrit le pilote de base de données à qui la source de données se connecte. Il peut être n’importe quel nom que vous choisissez.  
  
6.  Dans la boîte nom de l’utilisateur, tapez votre nom d’utilisateur de base de données (votre identifiant d’utilisateur de base de données).  
  
7.  Dans la boîte Server, tapez le pseudonyme de base de données ou connectez la chaîne pour le moteur Oracle Server que vous souhaitez accéder.  
  
8.  Cliquez sur OK pour ajouter cette source de données.  
  
> [!NOTE]  
>  La boîte de dialogue des sources de données apparaît, et l’administrateur de l’ODBC met à jour les informations du registre. Le nom d’utilisateur et la chaîne de connexion que vous avez tapé deviennent les valeurs de connexion par défaut pour cette source de données lorsque vous vous y connectez.  
  
1.  Cliquez sur Options faire plus de spécifications sur le pilote ODBC pour la configuration Oracle:  
  
    -   **Traduction** - Cliquez sur Sélectionnez pour choisir un traducteur de données chargé. La valeur \<par défaut n’est pas>.  
  
    -   **Performances** - Les REMARQUEs incluent dans la case à cocher des fonctions de catalogue précise si le conducteur retourne des colonnes de remarques pour l’ensemble de résultats [SQLColumns.](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md) Le pilote ODBC pour Oracle offre un accès plus rapide lorsque cette valeur n’est pas définie.  
  
         La liste de cocher de la colonnes de SQL indique si le conducteur renvoie les informations de la colonne. **La taille tampon** spécifie la taille, dans les octets, allouée pour recevoir des données récupérées. Le pilote optimise l’aller chercher de sorte que l’on se rende sur le serveur Oracle retourne suffisamment de lignes pour remplir un tampon de la taille spécifiée. Les valeurs plus grandes ont tendance à augmenter les performances lorsqu’elles obtiennent beaucoup de données.  
  
    -   **Personnalisation** - La case à cocher Standard Enforce ODBC DayOfWeek précise si l’ensemble de résultats sera conforme au format de jour de semaine spécifié par l’ODBC (dimanche et 1; Samedi 7). Si cette case à cocher est effacée, la valeur Oracle locale est retournée.  
  
         Le SQLDescribeCol **retourne toujours une valeur pour** la case à cocher de précision précise précise si oui ou non le conducteur doit retourner une valeur non-zéro pour *l’argument cbColDef* de **SQLDescribeCol**. Cet attribut de chaîne de connexion ne s’applique qu’aux colonnes où il n’y a pas d’échelle définie par Oracle, telles que les colonnes numériques calculées et les colonnes définies comme NUMBER sans précision ni échelle. Un appel **SQLDescribeCol** renvoie 130 pour la précision quand Oracle ne fournit pas cette information. Si cette case à cocher est effacée, le conducteur retournera 0 pour ces types de colonnes à la place.  
  
2.  Cliquez sur Ajouter pour ajouter une autre source de données, ou cliquez sur Près de la sortie.  
  
### <a name="to-modify-a-data-source-for-windows"></a>Modifier une source de données pour Windows  
  
1.  Ouvrez l’administrateur de source de données ODBC. Cliquez sur l’onglet DSN approprié.  
  
2.  Sélectionnez la source de données Oracle que vous souhaitez modifier, puis cliquez sur Configurer. La boîte de dialogue Microsoft ODBC pour Oracle Setup apparaît.  
  
3.  Modifier les champs de source de données applicables, puis cliquez sur OK.  
  
 Lorsque vous avez fini de modifier les informations contenues dans cette boîte de dialogue, l’administrateur de l’ODBC met à jour les informations du registre.
