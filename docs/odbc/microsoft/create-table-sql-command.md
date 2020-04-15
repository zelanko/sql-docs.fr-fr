---
title: TABLE CREATE - Commandement SQL Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- CREATE TABLE [ODBC]
ms.assetid: be2143ba-fc16-42c9-84f7-8985cd924860
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: dfc80a56a021b1bfeda38115e79f7086632900c8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298689"
---
# <a name="create-table---sql-command"></a>CREATE TABLE, commande SQL
Crée une table ayant les champs spécifiés.  
  
 Le Visual FoxPro ODBC Driver prend en charge la syntaxe en langue visuelle FoxPro native pour cette commande. Pour obtenir des renseignements spécifiques au conducteur, consultez **les remarques du conducteur**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CREATE TABLE | DBF TableName1 [NAME LongTableName] [FREE]  
   (FieldName1FieldType [(nFieldWidth [, nPrecision])]  
      [NULL | NOT NULL]   
      [CHECK lExpression1 [ERROR cMessageText1]]  
      [DEFAULT eExpression1]  
      [PRIMARY KEY | UNIQUE]  
      [REFERENCES TableName2 [TAG TagName1]]  
      [NOCPTRANS]  
   [, FieldName2 ...]  
      [, PRIMARY KEY eExpression2 TAG TagName2  
      |, UNIQUE eExpression3 TAG TagName3]  
      [, FOREIGN KEY eExpression4 TAG TagName4 [NODUP]  
            REFERENCES TableName3 [TAG TagName5]]  
      [, CHECK lExpression2 [ERROR cMessageText2]])  
| FROM ARRAY ArrayName  
```  
  
## <a name="arguments"></a>Arguments  
 TABLE CREATE &#124; DBF *TableName1*  
 Spécifie le nom de la table à créer. Les options TABLE et DBF sont identiques.  
  
 NOM *LongTableName*  
 Spécifie un long nom pour la table. Un nom de table longue ne peut être spécifié que lorsqu’une base de données est ouverte, car les noms de table longue sont stockés dans les bases de données.  
  
 Les noms longs peuvent contenir jusqu’à 128 caractères et peuvent être utilisés à la place de noms de fichiers courts dans la base de données.  
  
 FREE  
 Précise que la table ne sera pas ajoutée à une base de données ouverte. GRATUIT n’est pas nécessaire si une base de données n’est pas ouverte.  
  
 *(FieldName1 FieldType* [( *nFieldWidth* [, *nPrecision*])]  
 Spécifie le nom de champ, le type de champ, la largeur du champ et la précision du champ (nombre de décimales), respectivement.  
  
 *FieldType* est une seule lettre indiquant le type de [données](../../odbc/microsoft/visual-foxpro-field-data-types.md)du champ . Certains types de données sur le terrain exigent que vous spécifiiez *nFieldWidth* ou *nPrecision* ou les deux.  
  
 *nFieldWidth* et *nPrecision* sont ignorés pour D, G, I, L, M, P, T, et Y types. *nPrecision* par défaut à zéro (pas de décimales) si *nPrecision* n’est pas inclus pour les types B, F ou N.  
  
 NULL  
 Permet des valeurs nulles sur le terrain.  
  
 NOT NULL  
 Empêche les valeurs nulles sur le terrain.  
  
 Si vous ometez NULL et NOT NULL, le paramètre actuel de SET NULL détermine si les valeurs nulles sont autorisées sur le terrain. Toutefois, si vous ometez NULL et NOT NULL et incluez la clause PRIMARY KEY ou UNIQUE, le paramètre actuel de SET NULL est ignoré et le champ ne manque pas de NULL.  
  
 CHECK *lExpression1*  
 Spécifie une règle de validation pour le champ. *lExpression1* peut être une fonction définie par l’utilisateur. Chaque fois qu’un enregistrement vierge est joint, la règle de validation est vérifiée. Une erreur est générée si la règle de validation ne permet pas une valeur de champ vierge dans un enregistrement joint.  
  
 ERREUR *cMessageText1*  
 Spécifie le message d’erreur Visual FoxPro s’affiche lorsque la règle de champ génère une erreur. Le message n’est affiché que lorsque les données sont modifiées dans une fenêtre De navigation ou une fenêtre d’édition.  
  
 *EExpression DEFAULT1*  
 Spécifie une valeur par défaut pour le champ. Le type de données *d’eExpression1* doit être le même que le type de données du champ.  
  
 PRIMARY KEY  
 Crée un indice primaire pour le domaine. L’étiquette de l’index primaire a le même nom que le champ.  
  
 UNIQUE  
 Crée un index de candidat pour le domaine. L’étiquette d’index des candidats porte le même nom que le champ.  
  
> [!NOTE]  
>  Les index candidats (créés par l’option UNIQUE dans CREATE TABLE ou ALTER TABLE - SQL) ne sont pas les mêmes que les index créés avec l’option UNIQUE dans la commande INDEX. Un index créé avec l’option UNIQUE dans la commande INDEX permet des clés d’index en double; les index des candidats n’autorisent pas les clés d’index en double. Consultez [INDEX](../../odbc/microsoft/index-command.md) pour plus d’informations sur son option UNIQUE.  
  
 Les valeurs nulles et les enregistrements en double ne sont pas autorisés dans un domaine utilisé pour un indice primaire ou candidat. Cependant, Visual FoxPro ne générera pas d’erreur si vous créez un indice primaire ou candidat pour un domaine qui prend en charge les valeurs nulles. Visual FoxPro générera une erreur si vous tentez d’entrer une valeur nulle ou en double dans un champ utilisé pour un index primaire ou candidat.  
  
 REFERENCES *TableName2*[TAG *TagName1*]  
 Spécifie le tableau parent auquel une relation persistante est établie. Si vous omettez TAG *TagName1*, la relation est établie à l’aide de la clé d’index primaire de la table mère. Si le tableau parent n’a pas d’index primaire, Visual FoxPro génère une erreur.  
  
 Inclure TAG *TagName1* pour établir une relation basée sur une étiquette d’index existante pour le tableau parent. Les noms d’étiquettes d’index peuvent contenir jusqu’à 10 caractères.  
  
 La table mère ne peut pas être une table libre.  
  
 NOCPTRANS (NOCPTRANS)  
 Empêche la traduction à une page de code différente pour les champs de caractère et de mémo. Si le tableau est converti en une autre page de code, les champs pour lesquels NOCPTRANS a été spécifié ne sont pas traduits. NOCPTRANS ne peut être spécifié que pour les champs de caractère et de mémo.  
  
 L’exemple suivant crée une table nommée mytable contenant deux champs de caractères et deux champs de mémo. Le deuxième champ de caractère, char2, et le deuxième champ de notes, memo2, comprennent NOCPTRANS pour empêcher la traduction.  
  
```  
CREATE TABLE mytable (char1 C(10), char2 C(10) NOCPTRANS,;  
   memo1 M, memo2 M NOCPTRANS)  
```  
  
 PRIMARY KEY *eExpression2* TAG *TagName2*  
 Spécifie un indice primaire à créer. *eExpression2* spécifie tout champ ou combinaison de champs dans le tableau. TAG *TagName2* spécifie le nom de l’étiquette d’index primaire qui est créée. Les noms d’étiquettes d’index peuvent contenir jusqu’à 10 caractères.  
  
 Étant donné qu’un tableau ne peut avoir qu’un seul indice primaire, vous ne pouvez pas inclure cette clause si vous avez déjà créé un indice primaire pour un champ. Visual FoxPro génère une erreur si vous incluez plus d’une clause KEY PRIMARY dans CREATE TABLE.  
  
 *EExpression UNIQUE3*TAG *TagName3*  
 Crée un index de candidat. *eExpression3* spécifie tout champ ou combinaison de champs dans le tableau. Toutefois, si vous avez créé un indice primaire avec l’une des options KEY PRIMARY, vous ne pouvez pas inclure le champ qui a été spécifié pour l’indice primaire. TAG *TagName3* spécifie un nom d’étiquette pour l’étiquette d’index du candidat qui est créé. Les noms d’étiquettes d’index peuvent contenir jusqu’à 10 caractères.  
  
 Un tableau peut avoir plusieurs index candidats.  
  
 FOREIGN KEY *eExpression4*TAG *TagName4*[NODUP]  
 Crée un indice étranger (non primaire) et établit une relation avec une table mère. *eExpression4* spécifie l’expression clé de l’indice étranger, et *TagName4* spécifie le nom de l’étiquette de clé de l’index étranger qui est créée. Les noms d’étiquettes d’index peuvent contenir jusqu’à 10 caractères. Inclure NODUP pour créer un index étranger candidat.  
  
 Vous pouvez créer plusieurs index étrangers pour le tableau, mais les expressions de l’indice étranger doivent spécifier différents champs dans le tableau.  
  
 REFERENCES *TableName3*[TAG *TagName5*]  
 Spécifie le tableau parent auquel une relation persistante est établie. Inclure TAG *TagName5* pour établir une relation basée sur une étiquette d’index pour le tableau parent. Les noms d’étiquettes d’index peuvent contenir jusqu’à 10 caractères. Par défaut, si vous omettez TAG *TagName5,* la relation est établie à l’aide de la clé d’index primaire de la table mère.  
  
 CHECK *eExpression2*[ERROR *cMessageText2*]  
 Spécifie la règle de validation de table. ERROR *cMessageText2* spécifie le message d’erreur Visual FoxPro s’affiche lorsque la règle de validation de table est exécutée. Le message n’est affiché que lorsque les données sont modifiées dans une fenêtre De navigation ou une fenêtre d’édition.  
  
 DE ARRAY *ArrayName*  
 Spécifie le nom d’un tableau existant dont le contenu est le nom, le type, la précision et l’échelle pour chaque champ de la table. Le contenu du tableau peut être défini avec la fonction **AFIELDS**() .  
  
## <a name="remarks"></a>Notes  
 La nouvelle table est ouverte dans la zone de travail la plus basse disponible et peut être consultée par son alias. La nouvelle table est ouverte exclusivement, quel que soit le cadre actuel de SET EXCLUSIVE.  
  
 Si une base de données est ouverte et que vous n’incluez pas la clause GRATUIT, la nouvelle table est ajoutée à la base de données. Vous ne pouvez pas créer une nouvelle table du même nom qu’une table dans la base de données.  
  
 Si une base de données est ouverte, CREATE TABLE - SQL nécessite une utilisation exclusive de la base de données. Pour ouvrir une base de données à usage exclusif, incluez EXCLUSIF dans OPEN DATABASE.  
  
 Si une base de données n’est pas ouverte lorsque vous créez la nouvelle table, y compris les clauses NAME, CHECK, DEFAULT, FOREIGN KEY, PRIMARY KEY ou REFERENCES génèrent une erreur.  
  
> [!NOTE]  
>  LA syntaxe CREATE TABLE utilise des virgules pour séparer certaines options CREATE TABLE. En outre, la clause NULL, NOT NULL, CHECK, DEFAULT, PRIMARY KEY et UNIQUE doit être placée dans les parenthèses contenant les définitions de colonne.  
  
## <a name="driver-remarks"></a>Remarques du conducteur  
 Lorsque votre application envoie la déclaration ODBC SQL CREATE TABLE à la source de données, le visual FoxPro ODBC Driver traduit la commande dans la commande Visual FoxProCREATE TABLE à l’aide de la syntaxe indiquée dans le tableau suivant.  
  
|Syntaxe ODBC|Syntaxe visuelle FoxPro|  
|-----------------|--------------------------|  
|NOM *DE table de base* CREATE TABLE<br /><br /> (type*de données d’identification de colonne*<br /><br /> [PAS NUL]<br /><br /> [,*type de données d’identification de colonnes*<br /><br /> [PAS NUL] ...)|TABLE *TABLE DE CREATEName1* [NAME *LongTableName*]<br /><br /> (*FieldName1* *FieldType*<br /><br /> *[(nFieldWidth* [, *nPrecision]]*<br /><br /> [PAS NUL])|  
  
 Lorsque vous créez une table à l’aide du conducteur, le conducteur ferme la table immédiatement après la création pour permettre l’accès à la table par d’autres utilisateurs. Cela diffère de Visual FoxPro, qui laisse la table ouverte exclusivement sur la création. Toutefois, si une procédure stockée sur votre source de données contenant une instruction CREATE TABLE s’exécute, la table est laissée ouverte.  
  
 Si la source de données est une base de données (.dbc fichier), le visual FoxPro ODBC Driver crée une table nommée *LongTableName* avec le même nom que le *nom de table de base*.  
  
### <a name="using-data-definition-language-ddl"></a>Utilisation du langage de définition des données (DDL)  
 Vous ne pouvez pas inclure DDL dans les endroits suivants :  
  
-   Dans un relevé de SQL par lots qui nécessite une transaction  
  
-   En mode de validation manuelle, après une déclaration qui exigeait une transaction, à moins que votre application appelle **d’abord SQLTransact**.  
  
 Par exemple, si vous souhaitez créer une table temporaire, vous devez créer la table avant de commencer l’instruction nécessitant une transaction. Si vous incluez la déclaration CREATE TABLE dans un relevé SQL de lot qui nécessite une transaction, le conducteur renvoie un message d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER TABLE - Commandement SQL](../../odbc/microsoft/alter-table-sql-command.md)   
 [Types de données pris en charge (Visual FoxPro ODBC Driver)](../../odbc/microsoft/supported-data-types-visual-foxpro-odbc-driver.md)   
 [INSERT - Commandement SQL](../../odbc/microsoft/insert-sql-command.md)   
 [SELECT, commande SQL](../../odbc/microsoft/select-sql-command.md)
