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
manager: craigg
ms.openlocfilehash: 10e3726d26e03da2f9f731babc105244dbf1ff05
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52539782"
---
# <a name="data-returned-by-catalog-functions"></a>Données retournées par les fonctions de catalogue
Chaque fonction de catalogue retourne des données dans un jeu de résultats. Ce jeu de résultats n’est pas différent de tout autre ensemble de résultats. Il est généralement généré par prédéfini, paramétrés **sélectionnez** instruction qui est codé en dur dans le pilote ou stocké dans une procédure dans la source de données. Pour plus d’informations sur la façon de récupérer des données à partir d’un jeu de résultats, consultez [a un résultat défini créé ?](../../../odbc/reference/develop-app/was-a-result-set-created.md).  
  
 Le jeu de résultats pour chaque fonction de catalogue sont décrite dans l’entrée de référence pour cette fonction. Outre les colonnes répertoriées, le jeu de résultats peut contenir des colonnes spécifiques aux pilotes après la dernière colonne prédéfinie. Ces colonnes (le cas échéant) sont décrites dans la documentation du pilote.  
  
 Les applications doivent lier les colonnes spécifiques au pilote par rapport à la fin du jeu de résultats. Autrement dit, ils doivent calculer le nombre d’une colonne spécifiques au pilote en tant que le numéro de la dernière colonne - récupérée avec **SQLNumResultCols** - moins le nombre de colonnes qui se produisent après la colonne requise. Cela permet de gagner avoir à modifier l’application lorsque de nouvelles colonnes sont ajoutées au résultat défini dans les futures versions d’ODBC ou le pilote. Pour ce modèle fonctionne, pilotes doivent ajouter de nouvelles colonnes de spécifiques au pilote avant des colonnes spécifiques au pilote ancien afin que les numéros de colonne ne changent pas par rapport à la fin du jeu de résultats.  
  
 Les identificateurs qui sont retournées dans le jeu de résultats ne sont pas cités, même s’ils contiennent des caractères spéciaux. Par exemple, supposons que l’identificateur de caractère de guillemet (qui est spécifique au pilote et retournés via **SQLGetInfo**) est un guillemet double (") et la table comptes fournisseurs contient une colonne nommée Customer Name. Dans la ligne retournée par **SQLColumns** pour cette colonne, la valeur de la colonne de la TABLE_NAME est comptabilité, pas « comptabilité », et la valeur de la colonne COLUMN_NAME est le nom du client, pas « Customer Name ». Pour récupérer les noms des clients dans la table comptes fournisseurs, l’application serait citation ces noms :  
  
```  
SELECT "Customer Name" FROM "Accounts Payable"  
```  
  
 Pour plus d’informations, consultez [identificateurs entre guillemets](../../../odbc/reference/develop-app/quoted-identifiers.md).  
  
 Les fonctions de catalogue sont basées sur un modèle d’autorisation de type SQL dans laquelle une connexion est effectuée en fonction d’un nom d’utilisateur et le mot de passe, et uniquement les données pour lequel l’utilisateur a un privilège sont retournées. Mot de passe la protection des fichiers individuels, qui ne tient pas dans ce modèle, est définie par le pilote.  
  
 Les jeux de résultats retournés par les fonctions de catalogue sont presque jamais être mise à jour, et les applications ne doivent pas s’attendre à être en mesure de modifier la structure de la base de données en modifiant les données dans ces jeux de résultats.
