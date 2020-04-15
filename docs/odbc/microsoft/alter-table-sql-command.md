---
title: ALTER TABLE - Commandement SQL Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- alter table [ODBC]
ms.assetid: 3a01a291-f4d9-43bc-a725-5a95546ff364
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 587d721522503f9b392bb8be7433850fd7449efb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304710"
---
# <a name="alter-table---sql-command"></a>ALTER TABLE, commande SQL
Programmatique modifie la structure d’une table.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ALTER TABLE TableName1  
   ADD | ALTER [COLUMN] FieldName1  
      FieldType [(nFieldWidth [, nPrecision])]  
      [NULL | NOT NULL]  
      [CHECK lExpression1 [ERROR cMessageText1]]  
      [DEFAULT eExpression1]  
      [PRIMARY KEY | UNIQUE]  
      [REFERENCES TableName2 [TAG TagName1]]  
      [NOCPTRANS]  
 - Or -  
ALTER TABLE TableName1  
   ALTER [COLUMN] FieldName2  
      [NULL | NOT NULL]  
      [SET DEFAULT eExpression2]  
      [SET CHECK lExpression2 [ERROR cMessageText2]]  
      [DROP DEFAULT]  
      [DROP CHECK]  
 - Or -  
ALTER TABLE TableName1  
   [DROP [COLUMN] FieldName3]  
   [SET CHECK lExpression3 [ERROR cMessageText3]]  
   [DROP CHECK]  
   [ADD PRIMARY KEY eExpression3 TAG TagName2]  
   [DROP PRIMARY KEY]  
   [ADD UNIQUE eExpression4 [TAG TagName3]]  
   [DROP UNIQUE TAG TagName4]  
   [ADD FOREIGN KEY [eExpression5] TAG TagName4  
      REFERENCES TableName2 [TAG TagName5]]  
   [DROP FOREIGN KEY TAG TagName6 [SAVE]]  
   [RENAME COLUMN FieldName4 TO FieldName5]  
   [NOVALIDATE]  
```  
  
## <a name="arguments"></a>Arguments  
 *TableName1*  
 Précise le nom de la table dont la structure est modifiée.  
  
 ADD [COLUMN] *FieldName1*  
 Spécifie le nom du champ à ajouter.  
  
 ALTER [COLUMN] *FieldName1*  
 Spécifie le nom d’un champ existant à modifier.  
  
 *FieldType* *[(nFieldWidth* [, *nPrecision*]])  
 Spécifie le type de champ, la largeur du champ et la précision du champ (nombre de décimales) pour un champ nouveau ou modifié.  
  
 *FieldType* est une seule lettre qui indique le type de [données](../../odbc/microsoft/visual-foxpro-field-data-types.md)du champ . Certains types de données sur le terrain exigent que vous spécifiiez *nFieldWidth* ou *nPrecision* ou les deux.  
  
 *nFieldWidth* et *nPrecision* sont ignorés pour D, G, I, L, M, P, T, et Y types. Par défaut, *la nPrecision* est nulle (pas de décimales) si *la nPrecision* n’est pas incluse pour les types B, F ou N.  
  
 NULL &#124; NOT NULL  
 Permet ou empêche les valeurs nulles sur le terrain.  
  
 Si vous ometez NULL et NOT NULL, le paramètre actuel de SET NULL détermine si les valeurs nulles sont autorisées sur le terrain. Toutefois, si vous ometez NULL et NOT NULL et incluez la clause PRIMARY KEY ou UNIQUE, le paramètre actuel de SET NULL est ignoré et le champ n’est PAS NULL par défaut.  
  
 CHECK *lExpression1*  
 Spécifie une règle de validation pour le champ. *lExpression1* doit évaluer à une expression logique et peut être une fonction définie par l’utilisateur ou une procédure stockée. Chaque fois qu’un enregistrement vierge est joint, la règle de validation est vérifiée. Une erreur est générée si la règle de validation ne permet pas une valeur de champ vierge dans un enregistrement joint.  
  
 ERREUR *cMessageText1*  
 Spécifie le message d’erreur affiché lorsque la règle de validation sur le terrain génère une erreur.  
  
 *EExpression DEFAULT1*  
 Spécifie une valeur par défaut pour le champ. Le type de données *d’eExpression1* doit être le même que le type de données pour le champ.  
  
 PRIMARY KEY  
 Crée une étiquette d’index primaire. L’étiquette d’index a le même nom que le champ.  
  
 UNIQUE  
 Crée une étiquette d’index de candidat avec le même nom que le champ.  
  
> [!NOTE]  
>  Les index candidats (créés par l’option UNIQUE, prévu pour la compatibilité ANSI dans ALTER TABLE ou CREATE TABLE) diffèrent des index créés par l’utilisation de l’option UNIQUE dans la commande INDEX. Un index créé en utilisant UNIQUE dans la commande INDEX permet des clés index en double; les index des candidats n’autorisent pas les clés d’index en double.  
  
 Les valeurs nulles et les enregistrements en double ne sont pas autorisés dans un domaine qui est utilisé pour un indice primaire ou candidat.  
  
 Si vous créez un nouveau champ en utilisant ADD COLUMN, Visual FoxPro ne générera pas d’erreur si vous créez un index primaire ou candidat pour un champ qui prend en charge les valeurs nulles. Cependant, Visual FoxPro générera une erreur si vous essayez d’entrer une valeur nulle ou en double dans un champ qui est utilisé pour un index primaire ou candidat.  
  
 Si vous modifiez un champ existant et que l’expression de l’index primaire ou candidat se compose de champs dans le tableau, Visual FoxPro vérifie les champs pour voir s’ils contiennent des valeurs nulles ou des enregistrements en double. Si c’est le cas, Visual FoxPro génère une erreur et la table n’est pas modifiée.  
  
 TABLE *REFERENCESName2* TAG *TagName1*  
 Spécifie le tableau parent auquel une relation persistante est établie. TAG *TagName1* spécifie l’étiquette d’index de la table mère sur laquelle la relation est basée. Les noms d’étiquettes d’index peuvent contenir jusqu’à 10 caractères.  
  
 NOCPTRANS (NOCPTRANS)  
 Empêche la traduction à une page de code différente pour les champs de caractère et de mémo. Si le tableau est converti en une autre page de code, les champs pour lesquels NOCPTRANS a été spécifié ne sont pas traduits. NOCPTRANS ne peut être spécifié que pour les champs de caractère et de mémo.  
  
 L’exemple suivant crée une table nommée mytable qui contient deux champs de caractères et deux champs de mémo. Le deuxième champ de caractère, char2, et le deuxième champ de notes, memo2, comprennent NOCPTRANS pour empêcher la traduction.  
  
```  
CREATE TABLE mytable (char1 C(10), char2 C(10) NOCPTRANS,;  
   memo1 M, memo2 M NOCPTRANS)  
```  
  
 ALTER [COLUMN] *FieldName2*  
 Spécifie le nom d’un champ existant à modifier.  
  
 SET *DEFAULT eExpression2*  
 Spécifie une nouvelle valeur par défaut pour un champ existant. Le type de données *d’eExpression2* doit être le même que le type de données pour le champ.  
  
 SET CHECK *lExpression2*  
 Spécifie une nouvelle règle de validation pour un champ existant. *lExpression2* doit évaluer à une expression logique et peut être une fonction définie par l’utilisateur ou une procédure stockée.  
  
 ERREUR *cMessageText2*  
 Spécifie le message d’erreur affiché lorsque la règle de validation sur le terrain génère une erreur. Le message n’est affiché que lorsque les données sont modifiées dans une fenêtre Parcourir ou Modifier.  
  
 DROP DEFAULT  
 Supprime la valeur par défaut d’un champ existant.  
  
 DROP CHECK  
 Supprime la règle de validation d’un champ existant.  
  
 DROP [COLUMN] *FieldName3*  
 Spécifie un champ à retirer de la table. La suppression d’un champ de la table supprime également le paramètre de valeur par défaut du champ et la règle de validation du terrain.  
  
 Si la clé d’index ou les expressions de déclenchement font référence au champ, les expressions deviennent invalides lorsque le champ est supprimé. Dans ce cas, une erreur n’est pas générée lorsque le champ est supprimé, mais la clé d’index invalide ou les expressions de déclenchement généreront des erreurs au moment de l’exécution.  
  
 SET CHECK *lExpression3*  
 Spécifie la règle de validation de table. *lExpression3* doit évaluer à une expression logique et peut être une fonction définie par l’utilisateur ou une procédure stockée.  
  
 ERREUR *cMessageText3*  
 Spécifie le message d’erreur affiché lorsque la règle de validation de table génère une erreur. Le message n’est affiché que lorsque les données sont modifiées dans une fenêtre Parcourir ou Modifier.  
  
 DROP CHECK  
 Supprime la règle de validation de la table.  
  
 ADD PRIMARY KEY *eExpression3*TAG *TagName2*  
 Ajoute un index primaire à la table. *eExpression3* spécifie l’expression principale de l’index, et *TagName2* spécifie le nom de l’étiquette d’index primaire. Les noms d’étiquettes d’index peuvent contenir jusqu’à 10 caractères. Si TAG *TagName2* est omis et *eExpression3* est un champ unique, l’étiquette d’index primaire a le même nom que le champ spécifié dans *eExpression3*.  
  
 CLÉ PRIMAIRE DE CHUTE  
 Supprime l’index primaire et son étiquette d’index. Étant donné qu’une table ne peut avoir qu’une seule clé principale, il n’est pas nécessaire de spécifier le nom de la clé principale. La suppression de l’indice primaire supprime également toute relation persistante basée sur la clé principale.  
  
 ADD UNIQUE *eExpression4*[TAG *TagName3*]  
 Ajoute un index de candidat à la table. *eExpression4* spécifie l’expression clé de l’index du candidat, et *TagName3* spécifie le nom de l’étiquette d’index du candidat. Les noms d’étiquettes d’index peuvent contenir jusqu’à 10 caractères. Si vous omettez TAG *TagName3* et si *eExpression4* est un champ unique, l’étiquette d’index du candidat a le même nom que le champ spécifié dans *eExpression4*.  
  
 DROP UNIQUE TAG *TagName4*  
 Supprime l’index du candidat et son index. Étant donné qu’un tableau peut avoir plusieurs clés de candidat, vous devez spécifier le nom de l’étiquette d’index du candidat.  
  
 ADD FOREIGN KEY [ *eExpression5*] TAG *TagName4*  
 Ajoute un indice étranger (non primaire) à la table. *eExpression5* spécifie l’expression clé de l’indice étranger, et *TagName4* spécifie le nom de l’étiquette de l’indice étranger. Les noms d’étiquettes d’index peuvent contenir jusqu’à 10 caractères.  
  
 REFERENCES *TableName2*[TAG *TagName5*]  
 Spécifie le tableau parent auquel une relation persistante est établie. Inclure TAG *TagName5* pour établir une relation basée sur une étiquette d’index existante pour le tableau parent. Les noms d’étiquettes d’index peuvent contenir jusqu’à 10 caractères. Si vous omettez TAG *TagName5*, la relation est établie à l’aide de l’étiquette d’index principal de la table mère.  
  
 DROP FOREIGN KEY TAG *TagName6*[SAVE]  
 Supprime une clé étrangère dont l’index est *TagName6*. Si vous omettez SAVE, l’étiquette d’index est supprimée de l’indice structurel. Inclure SAVE pour empêcher la suppression de l’étiquette d’index de l’indice structurel.  
  
 RENAME COLUMN *FieldName4*TO *FieldName5*  
 Vous permet de changer le nom d’un champ dans la table. *FieldName4* spécifie le nom du champ qui est rebaptisé. *FieldName5* spécifie le nouveau nom du champ.  
  
> [!CAUTION]  
>  Faites preuve de prudence lors du changement de nom des champs de table parce que les expressions indexées, les règles, les commandes et les fonctions de validation de champ et de table peuvent faire référence aux noms de terrain originaux.  
  
 NOVALIDATE  
 Précise que Visual FoxPro permet d’apporter des modifications à la structure de la table; ces modifications peuvent violer l’intégrité des données dans le tableau. Par défaut, Visual FoxPro empêche ALTER TABLE d’apporter des modifications qui violent l’intégrité des données dans le tableau. Inclure NOVALIDATE pour remplacer ce comportement par défaut.  
  
## <a name="remarks"></a>Notes  
 ALTER TABLE peut être utilisé pour modifier la structure d’une table qui n’a pas été ajoutée à une base de données. Toutefois, Visual FoxPro génère une erreur si vous incluez les clauses DEFAULT, FOREIGN KEY, PRIMARY KEY, REFERENCES ou SET lors de la modification d’une table libre.  
  
 ALTER TABLE peut reconstruire la table en créant un nouvel en-tête de table et en apaisant les enregistrements sur l’en-tête de la table. Par exemple, le changement du type ou de la largeur d’un champ peut entraîner la reconstruction de la table.  
  
 Une fois qu’une table est reconstruite, des règles de validation de champ sont exécutées pour tous les champs dont le type ou la largeur est changé. Si vous modifiez le type ou la largeur d’un champ dans la table, la règle de table est exécutée.  
  
 Si vous modifiez les règles de validation de champ ou de table pour une table qui a des enregistrements, Visual FoxPro teste les nouvelles règles de validation de champ ou de table par rapport aux données existantes et émet un avertissement sur la première occurrence d’une règle de validation de champ ou de table ou d’une violation de déclenchement.  
  
 Si le tableau que vous modifiez se trouve dans une base de données, ALTER TABLE - SQL nécessite une utilisation exclusive de la base de données. Pour ouvrir une base de données à usage exclusif, incluez EXCLUSIF dans OPEN DATABASE.  
  
## <a name="see-also"></a>Voir aussi  
 [TABLE CREATE - Commandement SQL](../../odbc/microsoft/create-table-sql-command.md)   
 [INDEX, commande](../../odbc/microsoft/index-command.md)
