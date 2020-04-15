---
title: Données retournées par les fonctions de catalogue (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], result sets
- functions [ODBC], catalog functions
ms.assetid: 399e1a64-8766-4c44-81ff-445399b7a1de
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a0d9b63de04f79fd95c1b06d8e84d85c6f4fea02
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305226"
---
# <a name="data-returned-by-catalog-functions"></a>Données retournées par les fonctions de catalogue
Chaque fonction de catalogue renvoie les données à la suite de l’ensemble. Cet ensemble de résultats n’est pas différent de tout autre ensemble de résultats. Il est généralement généré par une déclaration **SELECT** prédéfinie et paramétrée qui est codée en dur dans le conducteur ou stockée dans une procédure dans la source de données. Pour plus d’informations sur la façon de récupérer les données d’un ensemble de résultats, voir [Était un ensemble de résultats créé?](../../../odbc/reference/develop-app/was-a-result-set-created.md).  
  
 L’ensemble de résultat pour chaque fonction de catalogue est décrit dans l’entrée de référence de cette fonction. En plus des colonnes énumérées, l’ensemble de résultats peut contenir des colonnes spécifiques au conducteur après la dernière colonne prédéfinie. Ces colonnes (le cas échéant) sont décrites dans la documentation du conducteur.  
  
 Les applications doivent lier les colonnes spécifiques au conducteur par rapport à la fin de l’ensemble de résultats. Autrement dit, ils devraient calculer le nombre d’une colonne spécifique au conducteur comme le nombre de la dernière colonne - récupéré avec **SQLNumResultCols** - moins le nombre de colonnes qui se produisent après la colonne requise. Cela permet d’économiser avoir à modifier l’application lorsque de nouvelles colonnes sont ajoutées au résultat défini dans les versions futures d’ODBC ou du pilote. Pour que ce système fonctionne, les conducteurs doivent ajouter de nouvelles colonnes spécifiques au conducteur avant les anciennes colonnes spécifiques au conducteur afin que les numéros de colonne ne changent pas par rapport à la fin de l’ensemble de résultats.  
  
 Les identifiants qui sont retournés dans l’ensemble de résultats ne sont pas cités, même s’ils contiennent des caractères spéciaux. Supposons, par exemple, que le caractère de citation d’identification (qui est spécifique au conducteur et retourné par **SQLGetInfo**) est une double marque de de cotation («) et le tableau comptes à payer contient une colonne nommée Nom du client. Dans la rangée retournée par **SQLColumns** pour cette colonne, la valeur de la colonne TABLE_NAME est comptes payables, pas "Comptes payables", et la valeur de la colonne COLUMN_NAME est le nom du client, pas "Nom du client". Pour récupérer les noms des clients dans le tableau des comptes à payer, l’application citerait ces noms :  
  
```  
SELECT "Customer Name" FROM "Accounts Payable"  
```  
  
 Pour plus d’informations, voir [Identifiers cités](../../../odbc/reference/develop-app/quoted-identifiers.md).  
  
 Les fonctions de catalogue sont basées sur un modèle d’autorisation de type SQL dans lequel une connexion est faite en fonction d’un nom d’utilisateur et d’un mot de passe, et seules les données pour lesquelles l’utilisateur a un privilège sont retournés. La protection par mot de passe des fichiers individuels, qui ne s’inscrit pas dans ce modèle, est définie par le conducteur.  
  
 Les ensembles de résultats retournés par les fonctions de catalogue ne sont presque jamais updatables, et les applications ne devraient pas s’attendre à être en mesure de modifier la structure de la base de données en modifiant les données dans ces ensembles de résultats.
