---
title: Données retournées par les fonctions de catalogue | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 14499071bd180a7ea709fda3eb26aeae46f229c7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68077023"
---
# <a name="data-returned-by-catalog-functions"></a>Données retournées par les fonctions de catalogue
Chaque fonction de catalogue retourne des données sous la forme d’un jeu de résultats. Ce jeu de résultats n’est pas différent de tout autre jeu de résultats. Elle est généralement générée par une instruction **Select** paramétrable prédéfinie qui est codée en dur dans le pilote ou stockée dans une procédure de la source de données. Pour plus d’informations sur la façon de récupérer des données à partir d’un jeu de résultats, consultez [was a-t-il créé un jeu de résultats ?](../../../odbc/reference/develop-app/was-a-result-set-created.md).  
  
 Le jeu de résultats pour chaque fonction de catalogue est décrit dans l’entrée de référence pour cette fonction. En plus des colonnes listées, le jeu de résultats peut contenir des colonnes spécifiques au pilote après la dernière colonne prédéfinie. Ces colonnes (le cas échéant) sont décrites dans la documentation du pilote.  
  
 Les applications doivent lier des colonnes spécifiques au pilote par rapport à la fin du jeu de résultats. Autrement dit, ils doivent calculer le numéro d’une colonne spécifique au pilote en tant que numéro de la dernière colonne Récupérée avec **SQLNumResultCols** -moins le nombre de colonnes qui se produisent après la colonne requise. Cela évite d’avoir à modifier l’application lorsque de nouvelles colonnes sont ajoutées au jeu de résultats dans les versions ultérieures d’ODBC ou du pilote. Pour que ce schéma fonctionne, les pilotes doivent ajouter de nouvelles colonnes spécifiques au pilote avant les anciennes colonnes spécifiques au pilote afin que les numéros de colonne ne soient pas modifiés par rapport à la fin du jeu de résultats.  
  
 Les identificateurs qui sont retournés dans le jeu de résultats ne sont pas placés entre guillemets, même s’ils contiennent des caractères spéciaux. Par exemple, supposons que le caractère d’identificateur guillemet (qui est spécifique au pilote et retourné via **SQLGetInfo**) soit un guillemet double (") et que la table Accounts payable contienne une colonne nommée Customer Name. Dans la ligne retournée par **SQLColumns** pour cette colonne, la valeur de la colonne table_name est Accounts payable, et non « Accounts payable », et la valeur de la colonne column_name est Customer Name et non « Customer Name ». Pour récupérer les noms des clients dans la table Accounts payable, l’application doit citer les noms suivants :  
  
```  
SELECT "Customer Name" FROM "Accounts Payable"  
```  
  
 Pour plus d’informations, consultez [identificateurs entre guillemets](../../../odbc/reference/develop-app/quoted-identifiers.md).  
  
 Les fonctions de catalogue sont basées sur un modèle d’autorisation de type SQL dans lequel une connexion est établie en fonction d’un nom d’utilisateur et d’un mot de passe, et seules les données pour lesquelles l’utilisateur a un privilège sont retournées. La protection par mot de passe de fichiers individuels, qui ne rentre pas dans ce modèle, est définie par le pilote.  
  
 Les jeux de résultats retournés par les fonctions de catalogue ne peuvent pratiquement jamais être mis à jour et les applications ne doivent pas être en mesure de modifier la structure de la base de données en modifiant les données dans ces jeux de résultats.
