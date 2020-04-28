---
title: Ajout et modification de sources de données à l’aide du programme d’installation | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81281409"
---
# <a name="adding-and-modifying-data-sources-using-setup"></a>Ajout et modification de sources de données via la configuration
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Une source de données identifie un chemin d’accès aux données qui peut inclure une bibliothèque réseau, un serveur, une base de données et d’autres attributs. dans ce cas, la source de données est le chemin d’accès à une base de données Oracle. Pour vous connecter à une source de données, le gestionnaire de pilotes recherche des informations de connexion spécifiques dans le Registre Windows.  
  
 L’entrée de Registre créée par l’administrateur de la source de données ODBC est utilisée par le gestionnaire de pilotes ODBC et les pilotes ODBC. Cette entrée contient des informations sur chaque source de données et son pilote associé. Avant de pouvoir vous connecter à une source de données, ses informations de connexion doivent être ajoutées au registre.  
  
 Pour ajouter et configurer des sources de données, utilisez l’administrateur de la [source de données ODBC](../../odbc/admin/odbc-data-source-administrator.md). L’administrateur ODBC met à jour vos informations de connexion à la source de données. À mesure que vous ajoutez des sources de données, l’administrateur ODBC met à jour les informations de Registre pour vous.  
  
### <a name="to-add-a-data-source-for-windows"></a>Pour ajouter une source de données pour Windows  
  
1.  Ouvrez l’administrateur de la source de données ODBC.  
  
2.  Dans la boîte de dialogue administrateur de sources de données ODBC, cliquez sur Ajouter. La boîte de dialogue créer une nouvelle source de données s’affiche.  
  
3.  Sélectionnez Microsoft ODBC pour Oracle, puis cliquez sur Terminer. La boîte de dialogue installation de Microsoft ODBC pour Oracle s’affiche.  
  
4.  Dans la zone nom de la source de données, tapez le nom de la source de données à laquelle vous souhaitez accéder. Il peut s’agir de n’importe quel nom de votre choix.  
  
5.  Dans la zone Description, tapez la description du pilote. Ce champ facultatif décrit le pilote de base de données auquel la source de données se connecte. Il peut s’agir de n’importe quel nom de votre choix.  
  
6.  Dans la zone nom d’utilisateur, tapez votre nom d’utilisateur de base de données (votre ID d’utilisateur de base de données).  
  
7.  Dans la zone serveur, tapez l’alias de base de données ou la chaîne de connexion pour le moteur Oracle Server auquel vous souhaitez accéder.  
  
8.  Cliquez sur OK pour ajouter cette source de données.  
  
> [!NOTE]  
>  La boîte de dialogue sources de données s’affiche et l’administrateur ODBC met à jour les informations du Registre. Le nom d’utilisateur et la chaîne de connexion que vous avez tapés deviennent les valeurs de connexion par défaut pour cette source de données lorsque vous vous y connectez.  
  
1.  Cliquez sur options apporter plus de spécifications sur l’installation du pilote ODBC pour Oracle :  
  
    -   **Traduction** -cliquez sur Sélectionner pour choisir un convertisseur de données chargé. La valeur par \<défaut est aucun> de traduction.  
  
    -   **Performances** -la case à cocher inclure les notes dans les fonctions de catalogue spécifie si le pilote retourne des colonnes de remarques pour le jeu de résultats [SQLColumns](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md) . Le pilote ODBC pour Oracle fournit un accès plus rapide lorsque cette valeur n’est pas définie.  
  
         La case à cocher inclure les SYNONYMEs dans les colonnes SQL spécifie si le pilote retourne des informations sur les colonnes. **Taille de la mémoire tampon** spécifie la taille, en octets, allouée à la réception des données extraites. Le pilote optimise l’extraction afin qu’une extraction à partir du serveur Oracle retourne suffisamment de lignes pour remplir une mémoire tampon de la taille spécifiée. Des valeurs plus élevées tendent à augmenter les performances lors de l’extraction d’un grand nombre de données.  
  
    -   **Personnalisation** : la case à cocher appliquer le standard ODBC DayOfWeek spécifie si le jeu de résultats est conforme au format de jour de la semaine spécifié par ODBC (dimanche = 1 ; Samedi = 7). Si cette case à cocher est désactivée, la valeur Oracle spécifique aux paramètres régionaux est retournée.  
  
         SQLDescribeCol **retourne toujours une valeur pour** la case à cocher précision spécifie si le pilote doit retourner une valeur différente de zéro pour l’argument *cbColDef* de **SQLDescribeCol**. Cet attribut de chaîne de connexion s’applique uniquement aux colonnes où aucune échelle n’est définie par Oracle, telles que les colonnes numériques calculées et les colonnes définies comme nombre sans précision ou échelle. Un appel de **SQLDescribeCol** retourne 130 pour la précision quand Oracle ne fournit pas ces informations. Si cette case à cocher est désactivée, le pilote retourne 0 pour ces types de colonnes à la place.  
  
2.  Cliquez sur Ajouter pour ajouter une autre source de données ou sur Fermer pour quitter.  
  
### <a name="to-modify-a-data-source-for-windows"></a>Pour modifier une source de données pour Windows  
  
1.  Ouvrez l’administrateur de la source de données ODBC. Cliquez sur l’onglet DSN approprié.  
  
2.  Sélectionnez la source de données Oracle que vous souhaitez modifier, puis cliquez sur Configurer. La boîte de dialogue installation de Microsoft ODBC pour Oracle s’affiche.  
  
3.  Modifiez les champs de source de données applicables, puis cliquez sur OK.  
  
 Lorsque vous avez fini de modifier les informations de cette boîte de dialogue, l’administrateur ODBC met à jour les informations du Registre.
