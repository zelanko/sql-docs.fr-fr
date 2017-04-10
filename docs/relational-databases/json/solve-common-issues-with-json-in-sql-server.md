---
title: "Forum Aux Questions concernant JSON dans SQL Server | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "07/07/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JSON, FORUM AUX QUESTIONS"
ms.assetid: feae120b-55cc-4601-a811-278ef1c551f9
caps.latest.revision: 9
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 9
---
# Forum Aux Questions concernant JSON dans SQL Server
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

 Vous pouvez trouver ici des réponses aux questions courantes sur la prise en charge de JSON intégrée à SQL Server.  
 
## Sortie FOR JSON et JSON

### FOR JSON PATH ou FOR JSON AUTO ?  
 **Question.** Je dois créer un résultat de texte JSON à partir d’une simple requête SQL sur une table unique. FOR JSON PATH et FOR JSON AUTO produisent le même résultat. Quelle option dois-je utiliser ?  
  
 **Réponse.** Utilisez FOR JSON PATH. Bien qu’il n’y ait aucune différence dans la sortie JSON, le mode AUTO intègre une logique supplémentaire qui vérifie si les colonnes doivent être imbriquées. Considérez PATH comme l’option par défaut.  

### Créer une structure JSON imbriquée  
 **Question.** Je dois produire un JSON complexe avec plusieurs tableaux au même niveau. FOR JSON PATH peut créer des objets imbriqués à l’aide de chemins d’accès, et FOR JSON AUTO crée un niveau d’imbrication supplémentaire pour chaque table. Aucune de ces deux options ne me permet de générer la sortie souhaitée. Comment puis-je créer un format JSON personnalisé que les options existantes ne prennent pas directement en charge ?  
  
 **Réponse.** Vous pouvez créer une structure de données en ajoutant des requêtes FOR JSON en tant qu’expressions de colonne qui retournent du texte JSON, ou créer un JSON manuellement en utilisant la fonction JSON_QUERY, comme dans l’exemple suivant.  
  
```tsql  
SELECT col1, col2, col3,  
             (SELECT col11, col12, col13 FROM t11 WHERE t11.FK = t1.PK FOR JSON PATH) as t11,  
             (SELECT col21, col22, col23 FROM t21 WHERE t21.FK = t1.PK FOR JSON PATH) as t21,  
             (SELECT col31, col32, col33 FROM t31 WHERE t31.FK = t1.PK FOR JSON PATH) as t31,  
             JSON_QUERY('{"'+col4'":"'+col5+'"}' as t41  
FROM t1  
FOR JSON PATH  
```  
  
Chaque résultat d’une requête FOR JSON ou de la fonction JSON_QUERY dans des expressions de colonne est mis en forme comme un sous-objet JSON imbriqué distinct et inclus dans le résultat principal.  

### Empêcher une double séquence d’échappement JSON dans une sortie FOR JSON  
 **Question.** J’ai du texte JSON stocké dans une colonne de table. Je souhaite l’inclure dans la sortie de FOR JSON. FOR JSON place tous les caractères dans une séquence d’échappement dans le JSON. J’obtiens donc une chaîne JSON au lieu d’un objet imbriqué, comme dans l’exemple suivant.  
  
```tsql  
SELECT 'Text' as myText, '{"day":23}' as myJson  
FOR JSON PATH  
```  
  
 Cette requête produit la sortie suivante :  
  
```json  
[{"myText":"Text","myJson":"{\"day\":23}"}]  
```  
  
 Comment éviter cela ? Je veux que `{"day":23}` soit retourné en tant qu’objet JSON, pas comme du texte dans une séquence d’échappement.  
  
 **Réponse.** Un objet JSON stocké dans une colonne de texte ou un littéral est traité comme n’importe quel texte. Il est entouré de guillemets doubles et placé dans une séquence d’échappement. Si vous voulez retourner un objet JSON sans séquence d’échappement, vous devez transmettre cette colonne en tant qu’argument à la fonction JSON_QUERY, comme illustré dans l’exemple suivant.  
  
```tsql  
SELECT col1, col2, col3, JSON_QUERY(jsoncol1) AS jsoncol1  
FROM tab1  
FOR JSON PATH  
```  
  
 JSON_QUERY sans son deuxième paramètre facultatif retourne uniquement le premier argument comme résultat. Étant donné que JSON_QUERY retourne un JSON valide, FOR JSON sait que ce résultat ne doit pas être placé dans une séquence d’échappement.

### Un JSON généré avec la clause WITHOUT_ARRAY_WRAPPER est placé dans une séquence d’échappement dans la sortie JSON  
 **Question.** J’essaie de mettre en forme une expression de colonne à l’aide de FOR JSON et de l’option WITHOUT_ARRAY_WRAPPER.  
  
```tsql  
SELECT 'Text' as myText,  
       (SELECT 12 day, 8 mon FOR JSON PATH, WITHOUT_ARRAY_WRAPPER) as myJson  
FOR JSON PATH   
```  
  
 Il semble que le texte retourné par la requête FOR JSON soit placé dans une séquence d’échappement en tant que texte brut. Cela se produit uniquement si WITHOUT_ARRAY_WRAPPER est spécifié. Pourquoi ce texte n’est-il pas considéré comme un objet JSON et inclus sans séquence d’échappement dans le résultat ?  
  
 **Réponse.** Si vous spécifiez l’option WITHOUT_ARRAY_WRAPPER, le texte JSON généré n’est pas nécessairement valide. Par conséquent, l’expression FOR JSON externe suppose qu’il s’agit de texte brut et place la chaîne dans une séquence d’échappement. Si vous êtes certain que la sortie JSON est valide, encapsulez-la avec la fonction JSON_QUERY afin de la promouvoir en tant que JSON de format correct, comme dans l’exemple suivant.  
  
```tsql  
SELECT 'Text' as myText,  
      JSON_QUERY((SELECT 12 day, 8 mon FOR JSON PATH, WITHOUT_ARRAY_WRAPPER)) as myJson  
FOR JSON PATH    
```  

## Entrée OPENJSON et JSON

### Retourner un sous-objet JSON imbriqué à partir d’un texte JSON avec OPENJSON  
 **Question.** Je ne parviens pas à ouvrir un tableau d’objet JSON complexe contenant les deux valeurs scalaires, des objets et des tableaux en utilisant OPENJSON avec un schéma explicite. Si référence une clé dans la clause WITH, seules les valeurs scalaires sont retournées. Les objets et tableaux sont retournés en tant que valeurs Null. Comment puis-je extraire des objets ou tableaux dans des objets JSON ?  
  
 **Réponse.** Si vous voulez retourner un objet ou tableau sous forme de colonne, utilisez l’option AS JSON dans la définition de colonne, comme dans l’exemple suivant.  
  
```tsql  
SELECT scalar1, scalar2, obj1, obj2, arr1  
FROM OPENJSON(@json)  
             WITH ( scalar1 int,  
                          scalar2 datetime2,  
                          obj1 NVARCHAR(MAX) AS JSON,  
                          obj2 NVARCHAR(MAX) AS JSON,  
                          arr1 NVARCHAR(MAX) AS JSON)  
```  

### Utiliser OPENJSON à la place de JSON_VALUE pour retourner des valeurs de texte long  
 **Question.** J’ai une clé description dans un texte JSON qui contient du texte long. `JSON_VALUE(@json, '$.description')` retourne la valeur NULL au lieu d’une valeur.  
  
 **Réponse.** JSON_VALUE est conçue pour retourner des valeurs scalaires courtes. En règle générale, la fonction retourne NULL au lieu d’une erreur de dépassement. Si vous voulez retourner des valeurs plus longues, utilisez OPENJSON, qui prend en charge les valeurs de NVARCHAR (MAX), comme dans l’exemple suivant.  
  
```tsql  
SELECT myText FROM OPENJSON(@json) WITH (myText NVARCHAR(MAX) '$.description')  
```  

### Utiliser OPENJSON à la place de JSON_VALUE pour gérer des clés en double  
 **Question.** J’ai des clés en double dans le texte JSON. JSON_VALUE retourne uniquement la première clé trouvée dans le chemin d’accès. Comment puis-je retrouver toutes les clés portant le même nom ?  
  
 **Réponse.** Les fonctions scalaires JSON intégrées retournent uniquement la première occurrence de l’objet référencé. Si vous avez besoin de plus d’une clé, utilisez la fonction table incluse OPENJSON, comme dans l’exemple suivant.  
  
```tsql  
SELECT value FROM OPENJSON(@json, '$.info.settings')  
WHERE [key] = 'color'  
```  

### OPENJSON requiert le niveau de compatibilité 130  
 **Question.** J’essaie d’exécuter OPENJSON dans SQL Server 2016, et j’obtiens l’erreur suivante.  
  
 `Msg 208, Level 16, State 1 ‘Invalid object name OPENJSON’`  
  
 **Réponse.** La fonction OPENJSON est disponible uniquement sous le niveau de compatibilité 130. Si votre base de données est associée à un niveau de compatibilité inférieure à 130, OPENJSON est masqué. Les autres fonctions JSON sont disponibles à tous les niveaux de compatibilité.  
 
## Autres questions

### Clés de référence contenant des caractères non alphanumériques dans du texte JSON  
 **Question.** J’ai des clés contenant des caractères non alphanumériques dans mon texte JSON. Comment puis-je référencer ces propriétés ?  
  
 **Réponse.** Vous devez les mettre entre guillemets dans les chemins d’accès JSON. Par exemple, `JSON_VALUE(@json, '$."$info"."First Name".value')`.
 