---
title: Programmation ADO Visual C++ | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ADO, Visual C++
- Visual C++ [ADO]
ms.assetid: 11233b96-e05c-4221-9aed-5f20944b0f1c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1890d554367b2a21bcd46a6d2ebddf00013957e6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67926422"
---
# <a name="visual-c-ado-programming"></a>Programmation ADO Visual C++
La référence d’API ADO décrit les fonctionnalités de l’application interface de programmation ADO (API) à l’aide d’une syntaxe similaire à Microsoft Visual Basic. Bien qu’elle s’adresse à tous les utilisateurs, les programmeurs ADO utilisent divers langages tels que Visual Basic, Visual C++ (avec et sans le **#import** directive) et Visual J ++ (avec le package de la classe ADO/WFC).  

> [!NOTE]
> Microsoft s’est terminée la prise en charge pour Visual J ++ en 2004.

 Pour prendre en compte cette diversité, le [ADO pour les index de syntaxe Visual C++](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-c.md) fournissent la syntaxe spécifique au langage de Visual C++ avec des liens vers des descriptions communes de fonctionnalités, paramètres, comportements exceptionnels et ainsi de suite, dans l’API Référence.  
  
 ADO est implémenté avec les interfaces COM (Component Object Model). Toutefois, il est plus facile pour les programmeurs de travailler avec COM dans certains langages de programmation que d’autres. Par exemple, presque tous les détails de l’utilisation de COM sont gérées implicitement pour les programmeurs Visual Basic, tandis que les programmeurs Visual C++ doivent gérer eux-mêmes ces détails.  
  
 Les sections suivantes résument les détails pour les programmeurs C et C++ à l’aide d’ADO et le **#import** directive. Il se concentre sur les types de données spécifiques à COM (**Variant**, **BSTR**, et **SafeArray**) et la gestion des erreurs (_com_error).  
  
## <a name="using-the-import-compiler-directive"></a>À l’aide de la Directive de compilateur #import  
 Le **#import** directive de compilateur Visual C++ simplifie l’utilisation avec les méthodes et propriétés ADO. La directive prend le nom d’un fichier contenant une bibliothèque de types, tels que le fichier .dll ADO (Msado15.dll) et génère des fichiers d’en-tête contenant des déclarations typedef, des pointeurs intelligents pour les interfaces et les constantes énumérées. Chaque interface est encapsulé ou encapsulée dans une classe.  
  
 Pour chaque opération dans une classe (autrement dit, un appel de méthode ou propriété), il existe une déclaration d’appeler directement l’opération (autrement dit, le formulaire « brut » de l’opération) et une déclaration pour appeler l’opération brute et lève une exception COM si l’opération ne parvient pas à exécuter succ essfully. Si l’opération est une propriété, il est généralement une directive de compilateur qui crée une autre syntaxe pour l’opération qui a une syntaxe comme Visual Basic.  
  
 Les opérations qui extraient la valeur d’une propriété ont un nom du formulaire, **obtenir**_propriété_. Les opérations qui définissent la valeur d’une propriété ont un nom du formulaire, **Put**_propriété_. Opérations qui définissent la valeur d’une propriété avec un pointeur vers un objet ADO ont des noms du formulaire, **PutRef**_propriété_.  
  
 Vous pouvez obtenir ou définir une propriété avec des appels des formes suivantes :  
  
```cpp
variable = objectPtr->GetProperty(); // get property value   
objectPtr->PutProperty(value);       // set property value  
objectPtr->PutRefProperty(&value);   // set property with object pointer  
```
  
## <a name="using-property-directives"></a>À l’aide de Directives de propriété  
 Le **__declspec(property...)**  directive de compilateur est une extension du langage C spécifiques à Microsoft qui déclare une fonction utilisée comme une propriété avec une syntaxe alternative. Par conséquent, vous pouvez définir ou obtenir les valeurs d’une propriété d’une manière similaire à Visual Basic. Par exemple, vous pouvez définir et obtenir une propriété de cette façon :  
  
```cpp
objectPtr->property = value;        // set property value  
variable = objectPtr->property;     // get property value  
```
  
 Notez que vous n’avez pas au code :  
  
```cpp
objectPtr->PutProperty(value);      // set property value  
variable = objectPtr->GetProperty;  // get property value  
```
  
 Le compilateur générera approprié **obtenir** _-_ , **Put**-, ou **PutRef**_propriété_ appel basé sur la syntaxe alternative est déclaré et indique si la propriété est en cours lues ou écrites.  
  
 Le **__declspec(property...)**  directive de compilateur peut déclarer uniquement **obtenir**, **put**, ou **obtenir** et **put** autre syntaxe pour une fonction. Opérations en lecture seule ont uniquement un **obtenir** déclaration ; les opérations d’écriture seule ont uniquement un **put** déclaration ; les opérations qui sont à la fois lire et écrire les deux ont **obtenir** et **put** déclarations.  
  
 Seules deux déclarations sont possibles avec cette directive ; Toutefois, chaque propriété peut avoir trois fonctions de propriété : **Obtenir**_propriété_, **Put**_propriété_, et **PutRef**_propriété_. Dans ce cas, seuls deux formes de la propriété possèdent une syntaxe alternative.  
  
 Par exemple, le **commande** objet **ActiveConnection** propriété est déclarée avec une syntaxe alternative pour **obtenir**_ActiveConnection_et **PutRef**_ActiveConnection_. Le **PutRef**-syntaxe est un bon choix, car dans la pratique, vous devez généralement placer une ouverture **connexion** objet (autrement dit, un **connexion** pointeur d’objet) dans ce propriété. En revanche, le **Recordset** objet a **obtenir**-, **Put**-, et **PutRef**_ActiveConnection_opérations, mais aucune autre syntaxe.  
  
## <a name="collections-the-getitem-method-and-the-item-property"></a>Collections, la méthode GetItem et la propriété d’élément  

 ADO définit plusieurs collections, notamment **champs**, **paramètres**, **propriétés**, et **erreurs**. Dans Visual C++, le **GetItem (_index_)** méthode retourne un membre de la collection. *Index* est un **Variant**, dont la valeur est soit un index numérique du membre dans la collection, soit une chaîne contenant le nom du membre.  
  
 Le **__declspec(property...)**  directive de compilateur déclare le **élément** une autre syntaxe pour chaque collection de la propriété de fondamentale **élémentaire GetItem()** (méthode). La syntaxe alternative utilise des crochets et ressemble à une référence de tableau. En règle générale, les deux formes de ressembler à ce qui suit :  
  
```cpp
  
      collectionPtr->GetItem(index);  
collectionPtr->Item[index];  
```
  
 Par exemple, affecter une valeur à un champ d’un **Recordset** objet, nommé  **_rs_** , dérivée de la **auteurs** table de la **pubs** base de données. Utilisez le **Item()** à accéder à la troisième propriété **champ** de la **Recordset** objet **champs** collection (collections sont indexées à partir de zéro ; Supposons que le troisième champ est nommé  **_Australie\_fname_** ). Appelez ensuite la **Value()** méthode sur le **champ** objet pour affecter une valeur de chaîne.  
  
 Cela peut être exprimé en Visual Basic dans le code suivant quatre façons (les deux derniers sont propres à Visual Basic ; les autres langages n’ont pas d’équivalents) :  
  
```cpp
rs.Fields.Item(2).Value = "value"  
rs.Fields.Item("au_fname").Value = "value"  
rs(2) = "value"  
rs!au_fname = "value"  
```
  
 L’équivalent dans Visual C++ pour les deux premiers formulaires ci-dessus est :  
  
```cpp
rs->Fields->GetItem(long(2))->PutValue("value");   
rs->Fields->GetItem("au_fname")->PutValue("value");  
```
  
 \- ou - (la syntaxe alternative de la **valeur** propriété est également affichée)  
  
```cpp
rs->Fields->Item[long(2)]->Value = "value";  
rs->Fields->Item["au_fname"]->Value = "value";  
```
  
 Pour obtenir des exemples d’itération sur une collection, consultez la section « Collections ADO » de « Référence ADO ».  
  
## <a name="com-specific-data-types"></a>Types de données spécifiques à COM  
 En général, n’importe quel type de données Visual Basic que vous trouver dans la référence d’API ADO a un équivalent Visual C++. Ceux-ci incluent des types de données standard comme **unsigned char** pour Visual Basic **octets**, **court** pour **entier**, et  **long** pour **Long**. Rechercher dans la syntaxe Indexesto voir exactement ce qui est nécessaire pour les opérandes d’une propriété ou une méthode donnée.  
  
 Les exceptions à cette règle sont les types de données spécifiques à COM : **Variant**, **BSTR**, et **SafeArray**.  
  
### <a name="variant"></a>Variant  
 Un **Variant** est un type de données structurées qui contient un membre de valeur et un membre de type de données. Un **Variant** peut contenir une grande variété d’autres types de données, y compris une autre variante, BSTR, Boolean, IDispatch ou IUnknown pointeur, devise, date et ainsi de suite. COM fournit également des méthodes qui facilitent le travail pour convertissent un type de données à un autre.  
  
 Le **_variant_t** classe encapsule et gère le **Variant** type de données.  
  
 Lorsque la référence de l’API ADO indique qu’une méthode ou l’opérande de la propriété prend une valeur, cela signifie généralement que la valeur est passée dans un **_variant_t**.  
  
 Cette règle est explicitement vrai quand le **paramètres** section dans les rubriques de la référence de l’API ADO indique qu’un opérande est un **Variant**. Une exception est lorsque la documentation indique explicitement que l’opérande utilise un type de données standard, tel que **Long** ou **octets**, ou une énumération. Une autre exception est lorsque l’opérande prend un **chaîne**.  
  
### <a name="bstr"></a>BSTR  
 Un **BSTR** (**B**asic **STR**ing) est un type de données structurées qui contient une chaîne de caractères et la longueur de la chaîne. COM fournit des méthodes pour allouer, manipuler et libérer un **BSTR**.  
  
 Le **_bstr_t** classe encapsule et gère le **BSTR** type de données.  
  
 Lorsque la référence de l’API ADO indique une méthode ou propriété prend un **chaîne** valeur, cela signifie que la valeur est sous la forme d’un **_bstr_t**.  
  
### <a name="casting-variantt-and-bstrt-classes"></a>Conversion des Classes _variant_t et _bstr_t  
 Fréquence à laquelle il n’est pas nécessaire de code explicitement un **_variant_t** ou **_bstr_t** dans un argument d’une opération. Si le **_variant_t** ou **_bstr_t** classe a un constructeur qui correspond au type de données de l’argument, le compilateur générera approprié **_variant_t** ou **_bstr_t**.  
  
 Toutefois, si l’argument est ambigu, autrement dit, type de données de l’argument correspond à plusieurs constructeurs, vous devez effectuer un cast de l’argument avec le type de données approprié pour appeler le constructeur approprié.  
  
 Par exemple, la déclaration pour le **Recordset::Open** méthode est :  
  
```cpp
    HRESULT Open (  
        const _variant_t & Source,  
        const _variant_t & ActiveConnection,  
        enum CursorTypeEnum CursorType,  
        enum LockTypeEnum LockType,  
        long Options );  
```
  
 Le `ActiveConnection` argument accepte une référence à un **_variant_t**, que vous pouvez coder comme une chaîne de connexion ou un pointeur vers une ouverture **connexion** objet.  
  
 La bonne **_variant_t** sera construite implicitement si vous passez une chaîne telle que «`DSN=pubs;uid=MyUserName;pwd=MyPassword;`», ou un pointeur tel que «`(IDispatch *) pConn`».  
  
> [!NOTE]
>  Si vous vous connectez à un fournisseur de source de données qui prend en charge l’authentification Windows, vous devez spécifier **Trusted_Connection = yes** ou **Integrated Security = SSPI** au lieu des ID d’utilisateur et mot de passe informations dans la chaîne de connexion.  
  
 Ou vous pouvez coder explicitement un **_variant_t** contenant un pointeur tel que «`_variant_t((IDispatch *) pConn, true)`». Le cast, `(IDispatch *)`, résout l’ambiguïté avec un autre constructeur qui accepte un pointeur vers une interface IUnknown.  
  
 Il est crucial, bien que rarement mentionné fait, que ADO est une interface IDispatch. Chaque fois qu’un pointeur vers un objet ADO doit être passé comme un **Variant**, ce pointeur doit être converti en un pointeur vers une interface IDispatch.  
  
 Le dernier cas est le deuxième argument booléen du constructeur avec sa valeur par défaut facultative explicitement codé `true`. Cet argument, le **Variant** constructeur à appeler son **AddRef**(méthode) (), qui compense ADO appeler automatiquement la **_variant_t::Release**méthode () Lorsque l’appel de méthode ou la propriété ADO est terminé.  
  
### <a name="safearray"></a>SafeArray  
 Un **SafeArray** est un type de données structurées qui contient un tableau d’autres types de données. Un **SafeArray** est appelée *safe* , car il contient des informations sur les limites de chaque dimension du tableau et limite l’accès aux éléments du tableau dans ces limites.  
  
 Lorsque la référence de l’API ADO indique qu’une méthode ou propriété prend ou retourne un tableau, cela signifie que la méthode ou propriété prend ou retourne un **SafeArray**, pas un tableau C/C++ natif.  
  
 Par exemple, le deuxième paramètre de la **connexion** objet **OpenSchema** méthode requiert un tableau de **Variant** valeurs. Ceux **Variant** valeurs doivent être passées en tant qu’éléments d’un **SafeArray**et qui **SafeArray** doit être défini comme la valeur d’un autre **Variant** . Il en est qu’autres **Variant** qui est passé comme deuxième argument de **OpenSchema**.  
  
 Exemples plus précisément, le premier argument de la **trouver** méthode est un **Variant** dont la valeur est une dimension **SafeArray**; chaque des première et deuxième arguments facultatifs de **AddNew** est une dimension **SafeArray**; et la valeur de retour de la **GetRows** méthode est un **Variant** dont la valeur est une à deux dimensions **SafeArray**.  
  
## <a name="missing-and-default-parameters"></a>Manquant et les paramètres par défaut  
 Visual Basic autorise les paramètres dans les méthodes manquants. Par exemple, le **Recordset** objet **Open** méthode ayant cinq paramètres, mais vous pouvez ignorer les paramètres intermédiaires et omettez les paramètres de fin. Une valeur par défaut **BSTR** ou **Variant** sera remplacée en fonction du type de données de l’opérande manquant.  
  
 En C/C++, vous doivent spécifier tous les opérandes. Si vous souhaitez spécifier un paramètre manquant dont le type de données est une chaîne, spécifiez un **_bstr_t** contenant une chaîne null. Si vous souhaitez spécifier un paramètre manquant dont le type de données est un **Variant**, spécifiez un **_variant_t** avec une valeur DISP_E_PARAMNOTFOUND et le type VT_ERROR. Vous pouvez également spécifier l’équivalent **_variant_t** constante, **vtMissing**, qui est fourni par le **#import** directive.  
  
 Trois méthodes sont des exceptions à l’utilisation classique de **vtMissing**. Il s’agit de la **Execute** méthodes de la **connexion** et **commande** objets et le **NextRecordset** procédé de la **Recordset** objet. Leurs signatures sont les suivantes :  
  
```cpp
_RecordsetPtr <A HREF="mdmthcnnexecute.htm">Execute</A>( _bstr_t CommandText, VARIANT * RecordsAffected,   
        long Options );  // Connection  
_RecordsetPtr <A HREF="mdmthcmdexecute.htm">Execute</A>( VARIANT * RecordsAffected, VARIANT * Parameters,   
        long Options );  // Command  
_RecordsetPtr <A HREF="mdmthnextrec.htm">NextRecordset</A>( VARIANT * RecordsAffected );  // Recordset  
```
  
 Les paramètres, *RecordsAffected* et *paramètres*, sont des pointeurs vers un **Variant**. *Paramètres* est un paramètre d’entrée qui spécifie l’adresse d’un **Variant** contenant un seul paramètre, ou tableau de paramètres, ce qui modifiera la commande en cours d’exécution. *RecordsAffected* est un paramètre de sortie qui spécifie l’adresse d’un **Variant**, où le nombre de lignes affectées par la méthode est retourné.  
  
 Dans le **commande** objet **Execute** (méthode), indiquer qu’aucun paramètre n’est spécifié en définissant *paramètres* soit `&vtMissing` (recommandé) ou le pointeur null (autrement dit, **NULL** ou zéro (0)). Si *paramètres* est défini pour le pointeur null, la méthode remplace en interne l’équivalent de **vtMissing**, puis termine l’opération.  
  
 Dans toutes les méthodes, indiquent que le nombre d’enregistrements affectés ne doit pas être retourné en définissant *RecordsAffected* au pointeur null. Dans ce cas, le pointeur null n’est pas bien un paramètre manquant comme une indication que la méthode doit ignorer le nombre d’enregistrements concernés.  
  
 Par conséquent, pour ces trois méthodes, il est valide pour un élément de code tel que :  
  
```cpp
pConnection->Execute("commandText", NULL, adCmdText);   
pCommand->Execute(NULL, NULL, adCmdText);  
pRecordset->NextRecordset(NULL);  
```
  
## <a name="error-handling"></a>Gestion des erreurs  
 Dans COM, la plupart des opérations renvoient un code de retour HRESULT qui indique si une fonction a été terminée avec succès. Le **#import** directive génère du code wrapper autour de chaque méthode « brut » ou une propriété et vérifie le HRESULT retourné. Si la valeur HRESULT indique un échec, le code wrapper génère une erreur COM en appelant _com_issue_errorex() avec le code de retour HRESULT en tant qu’argument. Objets d’erreur COM peuvent être interceptées dans un **essayez**-**catch** bloc. (Par souci d’efficacité, interceptez une référence à un **_com_error** objet.)  
  
 N’oubliez pas, il s’agit d’erreurs ADO : elles résultent de l’échec d’opération ADO. Les erreurs retournées par le fournisseur sous-jacent apparaissent sous la forme **erreur** des objets dans le **connexion** objet **erreurs** collection.  
  
 Le **#import** directive crée uniquement les erreurs des routines de gestion pour les méthodes et propriétés déclarées dans le fichier .dll ADO. Toutefois, vous pouvez tirer parti de cette erreur même mécanisme de gestion en écrivant votre propre fonction inline ou macro de vérification des erreurs. Consultez la rubrique [Extensions Visual C++](../../../ado/guide/appendixes/visual-c-extensions-for-ado.md), ou le code dans les sections suivantes pour obtenir des exemples.  
  
## <a name="visual-c-equivalents-of-visual-basic-conventions"></a>Équivalents Visual C++ des Conventions Visual Basic  
 Voici un récapitulatif de plusieurs conventions décrites dans la documentation ADO, codées dans Visual Basic, ainsi que leurs équivalents dans Visual C++.  
  
### <a name="declaring-an-ado-object"></a>Déclaration d’un objet ADO  
 En Visual Basic, une variable d’objet ADO (dans ce cas pour un **Recordset** objet) est déclarée comme suit :  
  
```vb
Dim rst As ADODB.Recordset  
```
  
 La clause, «`ADODB.Recordset`», est le ProgID de la **Recordset** tel que défini dans le Registre de l’objet. Une nouvelle instance d’un **enregistrement** objet est déclaré comme suit :  
  
```vb
Dim rst As New ADODB.Recordset  
```
  
 ou  
  
```vb
Dim rst As ADODB.Recordset  
Set rst = New ADODB.Recordset  
```
  
 Dans Visual C++, le **#import** directive génère des déclarations de type pointeur intelligent pour tous les objets ADO. Par exemple, une variable qui pointe vers un **_Recordset** objet est de type **_RecordsetPtr**et est déclarée comme suit :  
  
```cpp
_RecordsetPtr  rs;  
```
  
 Une variable qui pointe vers une nouvelle instance d’un **_Recordset** objet est déclaré comme suit :  
  
```cpp
_RecordsetPtr  rs("ADODB.Recordset");  
```
  
 ou  
  
```cpp
_RecordsetPtr  rs;  
rs.CreateInstance("ADODB.Recordset");  
```
  
 ou  
  
```cpp
_RecordsetPtr  rs;  
rs.CreateInstance(__uuidof(_Recordset));  
```
  
 Après le **CreateInstance** est appelée, la variable peut être utilisée comme suit :  
  
```cpp
rs->Open(...);  
```
  
 Notez que dans un cas, le «`.`« opérateur est utilisé comme si la variable était une instance d’une classe (`rs.CreateInstance`) et dans un autre cas, le «`->`» opérateur est utilisé comme si la variable était un pointeur vers une interface (`rs->Open`).  
  
 Une variable peut être utilisée de deux façons, car le «`->`» est surchargé pour permettre à une instance d’une classe se comporte comme un pointeur vers une interface. Un membre de classe privée de la variable d’instance contient un pointeur vers le **_Recordset** interface ; le «`->`« opérateur retourne ce pointeur ; et le pointeur retourné accède aux membres de la **_Recordset**  objet.  
  
### <a name="coding-a-missing-parameter---string"></a>Codage d’un paramètre manquant - chaîne  
 Lorsque vous devez coder l’absence d’un **chaîne** opérande en Visual Basic, vous simplement l’omettre. Vous devez spécifier l’opérande dans Visual C++. Code une **_bstr_t** qui a une chaîne vide en tant que valeur.  
  
```cpp
_bstr_t strMissing(L"");  
```
  
### <a name="coding-a-missing-parameter---variant"></a>Codage d’un paramètre manquant - Variant  
 Lorsque vous devez coder l’absence d’un **Variant** opérande en Visual Basic, vous simplement l’omettre. Vous devez spécifier tous les opérandes dans Visual C++. Absence de code **Variant** paramètre avec un **_variant_t** définir la valeur spéciale, DISP_E_PARAMNOTFOUND et le type VT_ERROR. Vous pouvez également spécifier **vtMissing**, qui est une constante prédéfinie équivalente fournie par le **#import** directive.  
  
```cpp
_variant_t  vtMissingYours(DISP_E_PARAMNOTFOUND, VT_ERROR);   
```
  
 \- ou -  
  
```cpp
...vtMissing...;  
```
  
### <a name="declaring-a-variant"></a>Déclaration d’un Variant  
 En Visual Basic, un **Variant** est déclaré avec le **Dim** instruction comme suit :  
  
```vb
Dim VariableName As Variant  
```
  
 Dans Visual C++, déclarez une variable en tant que type **_variant_t**. Quelques schématique **_variant_t** déclarations sont présentées ci-dessous.  
  
> [!NOTE]
>  Ces déclarations donnent simplement une vague idée de ce que vous codez dans votre propre programme. Pour plus d’informations, consultez les exemples ci-dessous et la documentation de Visual C++.  
  
```cpp
_variant_t  VariableName(value);  
_variant_t  VariableName((data type cast) value);  
_variant_t  VariableName(value, VT_DATATYPE);  
_variant_t  VariableName(interface * value, bool fAddRef = true);  
```
  
### <a name="using-arrays-of-variants"></a>À l’aide de tableaux de variantes  
 En Visual Basic, tableaux de **variantes** peuvent être codées avec le **Dim** instruction, ou vous pouvez utiliser la **tableau** fonctionner, comme illustré dans l’exemple de code suivant :  
  
```vb
Public Sub ArrayOfVariants  
Dim cn As ADODB.Connection  
Dim rs As ADODB.Recordset  
Dim fld As ADODB.Field  
  
    cn.Open "DSN=pubs"  
    rs = cn.OpenSchema(adSchemaColumns, _  
        Array(Empty, Empty, "authors", Empty))  
    For Each fld in rs.Fields  
        Debug.Print "Name = "; fld.Name  
    Next fld  
    rs.Close  
    cn.Close  
End Sub  
```
  
 L’élément visuel suivant C++ exemple montre comment utiliser un **SafeArray** utilisé avec un **_variant_t**.  
  
#### <a name="notes"></a>Notes  
 Les notes suivantes correspondent aux sections commentées dans l’exemple de code.  
  
1.  Une fois encore, la fonction inline TESTHR() est définie pour tirer parti du mécanisme de gestion des erreurs existant.  
  
2.  Vous devez uniquement un tableau unidimensionnel, afin de pouvoir utiliser **SafeArrayCreateVector**, au lieu de l’objectif général **SAFEARRAYBOUND** déclaration et **SafeArrayCreate** fonction. Voici ce que ce code ressemblerait à l’aide **SafeArrayCreate**:  
  
    ```cpp
       SAFEARRAYBOUND   sabound[1];  
       sabound[0].lLbound = 0;  
       sabound[0].cElements = 4;  
       pSa = SafeArrayCreate(VT_VARIANT, 1, sabound);  
    ```
  
3.  Le schéma identifié par la constante énumérée, **adSchemaColumns**, est associé à quatre colonnes de contrainte : Table_catalog, TABLE_SCHEMA, TABLE_NAME et COLUMN_NAME. Par conséquent, un tableau de **Variant** valeurs avec quatre éléments est créé. Ensuite, une valeur de contrainte qui correspond à la troisième colonne, TABLE_NAME, est spécifiée.  
  
     Le **Recordset** qui est retourné se compose de plusieurs colonnes, un sous-ensemble des colonnes de contrainte. Les valeurs des colonnes de contrainte pour chaque ligne retournée doivent être le même que les valeurs correspondantes de la contrainte.  
  
4.  Ceux qui connaissent **SAFEARRAY** peut-être surpris que **SafeArrayDestroy**() n’est pas appelé avant la sortie. En fait, l’appel **SafeArrayDestroy**() entraîne dans ce cas une exception au moment de l’exécution. La raison est que le destructeur de `vtCriteria` appellera **VariantClear**() lorsque le **_variant_t** est hors de portée, ce qui libère le **SafeArray**. Appel **SafeArrayDestroy**, sans effacer manuellement les **_variant_t**, provoquerait le destructeur essayer d’effacer un non valide **SafeArray** pointeur.  
  
     Si **SafeArrayDestroy** ont été appelée, le code ressemblerait à ceci :  
  
    ```cpp
          TESTHR(SafeArrayDestroy(pSa));  
       vtCriteria.vt = VT_EMPTY;  
          vtCriteria.parray = NULL;  
    ```
  
     Toutefois, il est beaucoup plus simple pour vous permettre du **_variant_t** gérer le **SafeArray**.  
  
```cpp
// Visual_CPP_ADO_Prog_1.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
// Note 1  
inline void TESTHR( HRESULT _hr ) {   
   if FAILED(_hr)   
      _com_issue_error(_hr);   
}  
  
int main() {  
   CoInitialize(NULL);  
   try {  
      _RecordsetPtr pRs("ADODB.Recordset");  
      _ConnectionPtr pCn("ADODB.Connection");  
      _variant_t vtTableName("authors"), vtCriteria;  
      long ix[1];  
      SAFEARRAY *pSa = NULL;  
  
      pCn->Provider = "sqloledb";  
      pCn->Open("Data Source='(local)';Initial Catalog='pubs';Integrated Security=SSPI", "", "", adConnectUnspecified);  
      // Note 2, Note 3  
      pSa = SafeArrayCreateVector(VT_VARIANT, 1, 4);  
      if (!pSa)   
         _com_issue_error(E_OUTOFMEMORY);  
  
      // Specify TABLE_NAME in the third array element (index of 2).   
      ix[0] = 2;        
      TESTHR(SafeArrayPutElement(pSa, ix, &vtTableName));  
  
      // There is no Variant constructor for a SafeArray, so manually set the   
      // type (SafeArray of Variant) and value (pointer to a SafeArray).  
  
      vtCriteria.vt = VT_ARRAY | VT_VARIANT;  
      vtCriteria.parray = pSa;  
  
      pRs = pCn->OpenSchema(adSchemaColumns, vtCriteria, vtMissing);  
  
      long limit = pRs->GetFields()->Count;  
      for ( long x = 0 ; x < limit ; x++ )  
         printf( "%d: %s\n", x + 1, ((char*) pRs->GetFields()->Item[x]->Name) );  
      // Note 4  
      pRs->Close();  
      pCn->Close();  
   }  
   catch (_com_error &e) {  
      printf("Error:\n");  
      printf("Code = %08lx\n", e.Error());  
      printf("Code meaning = %s\n", (char*) e.ErrorMessage());  
      printf("Source = %s\n", (char*) e.Source());  
      printf("Description = %s\n", (char*) e.Description());  
   }  
   CoUninitialize();  
}  
```
  
### <a name="using-property-getputputref"></a>À l’aide de la propriété Get/Put/PutRef  
 En Visual Basic, le nom d’une propriété n’est pas qualifié par si elle est récupérée ou attribuer une référence.  
  
```vb
Public Sub GetPutPutRef  
Dim rs As New ADODB.Recordset  
Dim cn As New ADODB.Connection  
Dim sz as Integer  
cn.Open "Provider=sqloledb;Data Source=yourserver;" & _  
         "Initial Catalog=pubs;Integrated Security=SSPI;"  
rs.PageSize = 10  
sz = rs.PageSize  
rs.ActiveConnection = cn  
rs.Open "authors",,adOpenStatic  
' ...  
rs.Close  
cn.Close  
End Sub  
```
  
 Cet exemple Visual C++ illustre le **obtenir**/**Put**/**PutRef**_propriété_.  
  
#### <a name="notes"></a>Notes  
 Les notes suivantes correspondent aux sections commentées dans l’exemple de code.  
  
1.  Cet exemple utilise deux formes d’un argument de chaîne manquante : une constante explicite, **strMissing**et une chaîne que le compilateur utilisera pour créer une table temporaire **_bstr_t** qui existe pour l’étendue de la  **Ouvrez** (méthode).  
  
2.  Il n’est pas nécessaire d’effectuer un cast de l’opérande de `rs->PutRefActiveConnection(cn)` à `(IDispatch *)` , car le type de l’opérande est déjà `(IDispatch *)`.  
  
```cpp
// Visual_CPP_ado_prog_2.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
int main() {  
   CoInitialize(NULL);  
   try {  
      _ConnectionPtr cn("ADODB.Connection");  
      _RecordsetPtr rs("ADODB.Recordset");  
      _bstr_t strMissing(L"");  
      long oldPgSz = 0, newPgSz = 5;  
  
      // Note 1  
      cn->Provider = "sqloledb";  
      cn->Open("Data Source='(local)';Initial Catalog=pubs;Integrated Security=SSPI;", strMissing, "", adConnectUnspecified);  
  
      oldPgSz = rs->GetPageSize();  
      // -or-  
      // oldPgSz = rs->PageSize;  
  
      rs->PutPageSize(newPgSz);  
      // -or-  
      // rs->PageSize = newPgSz;  
  
      // Note 2  
      rs->PutRefActiveConnection( cn );  
      rs->Open("authors", vtMissing, adOpenStatic, adLockReadOnly, adCmdTable);  
      printf("Original pagesize = %d, new pagesize = %d\n", oldPgSz, rs->GetPageSize());  
      rs->Close();  
      cn->Close();  
  
   }  
   catch (_com_error &e) {  
      printf("Description = %s\n", (char*) e.Description());  
   }  
   ::CoUninitialize();  
}  
```
  
### <a name="using-getitemx-and-itemx"></a>À l’aide de GetItem et élément [x]  
 Cet exemple Visual Basic illustre la syntaxe standard et alternative de **élément**().  
  
```vb
Public Sub GetItemItem  
Dim rs As New ADODB.Recordset  
Dim name as String  
rs = rs.Open "authors", "DSN=pubs;", adOpenDynamic, _  
         adLockBatchOptimistic, adTable  
name = rs(0)  
' -or-  
name = rs.Fields.Item(0)  
rs(0) = "Test"  
rs.UpdateBatch  
' Restore name  
rs(0) = name  
rs.UpdateBatch  
rs.Close  
End Sub  
```
  
 Cet exemple Visual C++ illustre **élément**.  
  
> [!NOTE]
>  La note suivante correspond aux sections commentées dans l’exemple de code :  Lorsque la collection est accessible avec **élément**, l’index, **2**, doivent être converties en **long** donc un constructeur approprié est appelé.  
  
```cpp
// Visual_CPP_ado_prog_3.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
void main() {  
   CoInitialize(NULL);  
   try {  
      _ConnectionPtr cn("ADODB.Connection");  
      _RecordsetPtr rs("ADODB.Recordset");  
      _variant_t vtFirstName;  
  
      cn->Provider = "sqloledb";  
      cn->Open("Data Source='(local)';Initial Catalog=pubs;Integrated Security=SSPI;", "", "", adConnectUnspecified);  
  
      rs->PutRefActiveConnection( cn );  
      rs->Open("authors", vtMissing, adOpenStatic, adLockOptimistic, adCmdTable);  
      rs->MoveFirst();  
  
      // Note 1. Get a field.  
      vtFirstName = rs->Fields->GetItem((long)2)->GetValue();  
      // -or-  
      vtFirstName = rs->Fields->Item[(long)2]->Value;  
  
      printf( "First name = '%s'\n", (char*)( (_bstr_t)vtFirstName) );  
  
      rs->Fields->GetItem((long)2)->Value = L"TEST";  
      rs->Update(vtMissing, vtMissing);  
  
      // Restore name  
      rs->Fields->GetItem((long)2)->PutValue(vtFirstName);  
      // -or-  
      rs->Fields->GetItem((long)2)->Value = vtFirstName;  
      rs->Update(vtMissing, vtMissing);  
      rs->Close();  
   }  
   catch (_com_error &e) {  
      printf("Description = '%s'\n", (char*) e.Description());  
   }  
   ::CoUninitialize();  
}  
```
  
### <a name="casting-ado-object-pointers-with-idispatch-"></a>Conversion de pointeurs d’objet ADO avec (IDispatch *)  
 L’exemple Visual C++ suivant illustre l’utilisation (IDispatch *) pour les pointeurs d’objet ADO cast.  
  
#### <a name="notes"></a>Notes  
 Les notes suivantes correspondent aux sections commentées dans l’exemple de code.  
  
1.  Spécifiez une ouverture **connexion** objet dans un explicitement codé **Variant**. Effectuer un cast avec (IDispatch \*) afin du bon constructeur est appelé. En outre, définissez explicitement la seconde **_variant_t** paramètre à la valeur par défaut de **true**, de sorte que le décompte de références d’objet soit correct lorsque la **Recordset::Open** opération se termine.  
  
2.  L’expression, `(_bstr_t)`, n’est pas un cast, mais un **_variant_t** opérateur extrait un **_bstr_t** chaîne à partir de la **Variant** retourné par **valeur** .  
  
 L’expression, `(char*)`, n’est pas un cast, mais un **_bstr_t** opérateur qui extrait un pointeur vers la chaîne encapsulée dans un **_bstr_t** objet.  
  
 Cette section de code illustre certains comportements utiles de **_variant_t** et **_bstr_t** opérateurs.  
  
```cpp
// Visual_CPP_ado_prog_4.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
int main() {  
   CoInitialize(NULL);  
   try {  
      _ConnectionPtr pConn("ADODB.Connection");  
      _RecordsetPtr pRst("ADODB.Recordset");  
  
      pConn->Provider = "sqloledb";  
      pConn->Open("Data Source='(local)';Initial Catalog='pubs';Integrated Security=SSPI", "", "", adConnectUnspecified);  
  
      // Note 1.  
      pRst->Open("authors", _variant_t((IDispatch *) pConn, true), adOpenStatic, adLockReadOnly, adCmdTable);  
      pRst->MoveLast();  
  
      // Note 2.  
      printf("Last name is '%s %s'\n",   
         (char*) ((_bstr_t) pRst->GetFields()->GetItem("au_fname")->GetValue()),  
         (char*) ((_bstr_t) pRst->Fields->Item["au_lname"]->Value));  
  
      pRst->Close();  
      pConn->Close();  
   }  
   catch (_com_error &e) {  
      printf("Description = '%s'\n", (char*) e.Description());  
   }     
   ::CoUninitialize();  
}  
```
