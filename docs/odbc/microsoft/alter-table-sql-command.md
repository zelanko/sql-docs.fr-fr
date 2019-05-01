---
title: ALTER TABLE, commande SQL | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5f656396455a8d5669debc158c3edc866491fcb5
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63457625"
---
# <a name="alter-table---sql-command"></a>ALTER TABLE, commande SQL
Modifie par programmation la structure d’une table.  
  
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
 Spécifie le nom de la table dont la structure est modifiée.  
  
 ADD [COLUMN] *FieldName1*  
 Spécifie le nom du champ à ajouter.  
  
 ALTER [COLUMN] *FieldName1*  
 Spécifie le nom d’un champ existant à modifier.  
  
 *FieldType* [( *nFieldWidth* [, *nPrecision*]])  
 Spécifie le type de champ, de la largeur de champ et de la précision du champ (nombre de décimales) pour un champ de nouveaux ou modifié.  
  
 *FieldType* est une lettre unique qui indique le champ [type de données](../../odbc/microsoft/visual-foxpro-field-data-types.md). Certains types de données de champ nécessitent que vous spécifiez *nFieldWidth* ou *nPrecision* ou les deux.  
  
 *nFieldWidth* et *nPrecision* sont ignorés pour D, G, I, L, M, P, T et Y types. Par défaut, *nPrecision* n’est zéro (aucun décimales) si *nPrecision* n’est pas inclus pour les types B, F ou N.  
  
 NULL &#124; NOT NULL  
 Autorise ou empêche des valeurs null dans le champ.  
  
 Si vous omettez la valeur NULL et NOT NULL, la valeur actuelle de SET NULL détermine si les valeurs null sont autorisées dans le champ. Toutefois, si vous omettez la valeur NULL et non NULL et incluez la clé primaire ou une clause UNIQUE, le paramètre actuel de la valeur NULL est ignoré et le champ n’est pas NULL par défaut.  
  
 Vérifiez *lExpression1*  
 Spécifie une règle de validation pour le champ. *lExpression1* doit correspondre à une expression logique et peut être une fonction définie par l’utilisateur ou une procédure stockée. Dès qu’un enregistrement vide est ajouté, la règle de validation est activée. Une erreur est générée si la règle de validation n’autorise pas une valeur de champ vide dans un enregistrement ajouté.  
  
 ERREUR *cMessageText1*  
 Spécifie le message d’erreur affiché lorsque la règle de validation de champ génère une erreur.  
  
 Par défaut *eExpression1*  
 Spécifie une valeur par défaut pour le champ. Le type de données de *eExpression1* doit être le même que le type de données pour le champ.  
  
 PRIMARY KEY  
 Crée une balise de l’index primaire. La balise d’index porte le même nom que le champ.  
  
 UNIQUE  
 Crée une balise d’index de candidat avec le même nom que le champ.  
  
> [!NOTE]  
>  Candidat index (créés en incluant l’option UNIQUE, fournie pour la compatibilité ANSI dans ALTER TABLE ou CREATE TABLE) diffèrent des index créés à l’aide de l’option UNIQUE dans la commande de l’INDEX. Un index créé à l’aide de UNIQUE dans la commande de l’INDEX autorise les clés d’index en double ; index candidats n’autorisent pas les clés d’index en double.  
  
 Les valeurs NULL et les enregistrements en double ne sont pas autorisées dans un champ qui est utilisé pour un index primaire ou candidate.  
  
 Si vous créez un nouveau champ à l’aide d’ajouter une colonne, Visual FoxPro ne générera pas une erreur si vous créez un index primaire ou candidate pour un champ qui prend en charge les valeurs null. Toutefois, Visual FoxPro génère une erreur si vous essayez d’entrer une valeur null ou en double dans un champ qui est utilisé pour un index primaire ou candidate.  
  
 Si vous modifiez un champ existant et le site principal ou expression d’index candidats se compose de champs dans la table, Visual FoxPro vérifie les champs pour voir si elles contiennent des valeurs null ou des enregistrements en double. S’ils le font, Visual FoxPro génère une erreur et la table n’est pas modifiée.  
  
 RÉFÉRENCES *TableName2* balise *TagName1*  
 Spécifie la table parente à laquelle une relation persistante est établie. BALISE *TagName1* spécifie la balise d’index de la table parent sur laquelle repose la relation. Noms de balise d’index peuvent contenir jusqu'à 10 caractères.  
  
 NOCPTRANS  
 Empêche la traduction vers différentes pages de codes pour les champs de caractère et Mémo. Si la table est convertie en une autre page de codes, les champs pour lesquels NOCPTRANS a été spécifié ne sont pas traduits. NOCPTRANS peut être spécifié uniquement pour les champs de caractère et Mémo.  
  
 L’exemple suivant crée une table nommée mytable qui contient deux champs de caractère et deux champs de type Mémo. Le deuxième champ de caractère, char2 et le deuxième champ de type Mémo, memo2, inclure NOCPTRANS pour empêcher la traduction.  
  
```  
CREATE TABLE mytable (char1 C(10), char2 C(10) NOCPTRANS,;  
   memo1 M, memo2 M NOCPTRANS)  
```  
  
 ALTER [COLUMN] *FieldName2*  
 Spécifie le nom d’un champ existant à modifier.  
  
 DÉFINIR par défaut *eExpression2*  
 Spécifie une nouvelle valeur par défaut pour un champ existant. Le type de données de *eExpression2* doit être le même que le type de données pour le champ.  
  
 VÉRIFICATION de l’ensemble *lExpression2*  
 Spécifie une nouvelle règle de validation pour un champ existant. *lExpression2* doit correspondre à une expression logique et peut être une fonction définie par l’utilisateur ou une procédure stockée.  
  
 ERREUR *cMessageText2*  
 Spécifie le message d’erreur affiché lorsque la règle de validation de champ génère une erreur. Le message s’affiche uniquement lorsque les données sont modifiées dans une fenêtre de navigation ou de modification.  
  
 DROP DEFAULT  
 Supprime la valeur par défaut pour un champ existant.  
  
 VÉRIFICATION DE LA LISTE  
 Supprime la règle de validation pour un champ existant.  
  
 DROP [COLUMN] *FieldName3*  
 Spécifie un champ à supprimer de la table. Suppression d’un champ de la table supprime également la valeur de la valeur par défaut et la règle de validation de champ.  
  
 Si l’index clé ou déclencheur expressions font référence au champ, les expressions deviennent non valides lorsque le champ est supprimé. Dans ce cas, une erreur n’est pas générée lorsque le champ est supprimé, mais les expressions de clé ou d’un déclencheur des index non valide génère des erreurs au moment de l’exécution.  
  
 VÉRIFICATION de l’ensemble *lExpression3*  
 Spécifie la règle de validation de table. *lExpression3* doit correspondre à une expression logique et peut être une fonction définie par l’utilisateur ou une procédure stockée.  
  
 ERREUR *cMessageText3*  
 Spécifie le message d’erreur affiché lorsque la règle de validation de table génère une erreur. Le message s’affiche uniquement lorsque les données sont modifiées dans une fenêtre de navigation ou de modification.  
  
 VÉRIFICATION DE LA LISTE  
 Supprime la règle de validation de la table.  
  
 Ajouter une clé primaire *eExpression3*balise *TagName2*  
 Ajoute un index primaire à la table. *eExpression3* Spécifie l’expression de clé de l’index primaire, et *TagName2* Spécifie le nom de la balise de l’index primaire. Noms de balise d’index peuvent contenir jusqu'à 10 caractères. Si balise *TagName2* est omis et *eExpression3* est un champ unique, la balise de l’index primaire porte le même nom que le champ spécifié dans *eExpression3*.  
  
 SUPPRIMER LA CLÉ PRIMAIRE  
 Supprime l’index primaire et sa balise de l’index. Une table peut avoir qu’une seule clé primaire, il n’est pas nécessaire de spécifier le nom de la clé primaire. Suppression de l’index primaire supprime également toutes les relations persistantes en fonction de la clé primaire.  
  
 Ajouter UNIQUE *eExpression4*[balise *TagName3*]  
 Ajoute un index de candidat à la table. *eExpression4* Spécifie l’expression d’index clé candidate, et *TagName3* Spécifie le nom de la balise d’index candidats. Noms de balise d’index peuvent contenir jusqu'à 10 caractères. Si vous omettez la balise *TagName3* et si *eExpression4* est un champ unique, la balise d’index de candidat a le même nom que le champ spécifié dans *eExpression4*.  
  
 BALISE UNIQUE DROP *TagName4*  
 Supprime l’index de candidat et sa balise de l’index. Comme une table peut avoir plusieurs clés candidates, vous devez spécifier le nom de la balise d’index candidats.  
  
 Ajouter une clé étrangère [ *eExpression5*] balise *TagName4*  
 Ajoute un index (non essentielles) étrangère à la table. *eExpression5* Spécifie l’expression de clé étrangère d’index, et *TagName4* Spécifie le nom de la balise de l’index étranger. Noms de balise d’index peuvent contenir jusqu'à 10 caractères.  
  
 RÉFÉRENCES *TableName2*[balise *TagName5*]  
 Spécifie la table parente à laquelle une relation persistante est établie. Inclure la balise *TagName5* pour établir une relation basée sur une balise d’index existante pour la table parente. Noms de balise d’index peuvent contenir jusqu'à 10 caractères. Si vous omettez la balise *TagName5*, la relation est établie à l’aide de la balise d’index primaire de la table parente.  
  
 BALISE de clé étrangère DROP *TagName6*[Enregistrer]  
 Supprime une clé étrangère dont l’étiquette index est *TagName6*. Si vous omettez d’enregistrement, la balise de l’index est supprimée de l’index structurel. Inclure enregistrer pour empêcher la suppression de la balise de l’index de l’index structurel.  
  
 RENAME COLUMN *FieldName4*TO *FieldName5*  
 Vous permet de modifier le nom d’un champ dans la table. *FieldName4* Spécifie le nom du champ qui est renommé. *FieldName5* Spécifie le nouveau nom du champ.  
  
> [!CAUTION]  
>  Soyez vigilant lorsque vous renommez des champs de la table, car les expressions d’index, les règles de validation de champ et de table, les commandes et les fonctions peuvent référencer les noms de champ d’origine.  
  
 NOVALIDATE  
 Spécifie que Visual FoxPro autorise les modifications à apporter à la structure de la table ; ces modifications peuvent violer l’intégrité des données dans la table. Par défaut, Visual FoxPro empêche l’apport de modifications qui enfreignent l’intégrité des données dans la table de ALTER TABLE. Inclure NOVALIDATE pour remplacer ce comportement par défaut.  
  
## <a name="remarks"></a>Notes  
 ALTER TABLE peut être utilisée pour modifier la structure d’une table qui n’a pas été ajoutée à une base de données. Toutefois, Visual FoxPro génère une erreur si vous incluez par défaut, FOREIGN KEY, PRIMARY KEY, références ou clauses SET lors de la modification d’une table gratuite.  
  
 ALTER TABLE peut reconstruire la table en créant un nouvel en-tête de table et en ajoutant des enregistrements à l’en-tête du tableau. Par exemple, la modification d’un champ de type ou de la largeur peut entraîner la table à reconstruire.  
  
 Une fois une table est reconstruite, les règles de validation de champ sont exécutés pour tous les champs dont la largeur ou type sont modifiés. Si vous modifiez le type ou la largeur de n’importe quel champ de la table, la règle de la table est exécutée.  
  
 Si vous modifiez des règles de validation de champ ou une table pour une table comportant des enregistrements, Visual FoxPro teste les règles de validation du champ ou les nouvelles sur les données existantes et émet un avertissement sur la première occurrence d’une règle de validation de champ ou une table ou d’une violation du déclencheur.  
  
 Si la table que vous modifiez est dans une base de données, ALTER TABLE - SQL requiert une utilisation exclusive de la base de données. Pour ouvrir une base de données pour un usage exclusif, inclure exclusif dans ouvrir la base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE TABLE, commande SQL](../../odbc/microsoft/create-table-sql-command.md)   
 [INDEX, commande](../../odbc/microsoft/index-command.md)
