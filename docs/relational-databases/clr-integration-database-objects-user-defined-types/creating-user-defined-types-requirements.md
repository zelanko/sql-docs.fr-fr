---
title: Exigences relatives au type défini par l’utilisateur | Microsoft Docs
description: Cet article décrit les décisions de conception importantes que vous devez prendre lorsque vous créez un type défini par l’utilisateur (UDT) à installer sur SQL Server.
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- UDTs [CLR integration], requirements
- serialization
- Native serialization format [CLR integration]
- attributes [CLR integration]
- XML serialization [CLR integration]
- user-defined types [CLR integration], requirements
- user-defined serialization [CLR integration]
- user-defined types [CLR integration], Native serialization
- UDTs [CLR integration], Native serialization
ms.assetid: bedc3372-50eb-40f2-bcf2-d6db6a63b7e6
author: rothja
ms.author: jroth
ms.openlocfilehash: b20192a3804dfba713b04706d528738ceb8768c3
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727815"
---
# <a name="creating-user-defined-types---requirements"></a>Création de types définis par l’utilisateur - Exigences
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Vous devez prendre plusieurs décisions importantes en matière de conception lors de la création d’un type défini par l’utilisateur (UDT) à installer dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour la plupart des types définis par l'utilisateur, il est recommandé de créer un type défini par l'utilisateur sous forme de structure mais il est également possible de le créer sous forme de classe. La définition de l'UDT doit être conforme aux spécifications de création d'UDT afin de pouvoir l'enregistrer avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="requirements-for-implementing-udts"></a>Configuration requise pour l'implémentation des types définis par l'utilisateur  
 Pour s'exécuter dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], votre UDT doit implémenter les éléments requis suivants dans sa définition :  
  
 Le type défini par l’utilisateur doit spécifier **Microsoft. SqlServer. Server. SqlUserDefinedTypeAttribute**. L’utilisation de **System. SerializableAttribute** est facultative, mais recommandée.  
  
-   Le type défini par l’utilisateur doit implémenter l’interface **System. Data. SqlTypes. INullable** dans la classe ou la structure en créant une méthode null **statique** publique (**Shared** in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic). **Null** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est par défaut compatible avec la valeur NULL. Ceci est nécessaire pour que le code exécuté dans l'UDT puisse être en mesure de reconnaître une valeur NULL.  
  
-   L’UDT doit contenir une méthode d' **analyse** **statique** publique (ou **partagée**) qui prend en charge l’analyse de, et une méthode **ToString** publique pour la conversion en une représentation sous forme de chaîne de l’objet.  
  
-   Un UDT avec un format de sérialisation défini par l’utilisateur doit implémenter l’interface **System. Data. IBinarySerialize** et fournir une méthode de **lecture** et d' **écriture** .  
  
-   L’UDT doit implémenter **System.Xml. Serialization. IXmlSerializable**, ou tous les champs et propriétés publics doivent être de types qui sont SÉRIALISABLES XML ou décorés avec l’attribut **XmlIgnore** si la substitution de la sérialisation standard est requise.  
  
-   Chaque objet UDT doit être soumis à une seule sérialisation. La validation échoue si les routines de sérialisation ou désérialisation reconnaissent plusieurs représentations d'un objet en particulier.  
  
-   **SqlUserDefinedTypeAttribute. IsByteOrdered** doit avoir la **valeur true** pour comparer les données dans l’ordre des octets. Si l’interface IComparable n’est pas implémentée et que **SqlUserDefinedTypeAttribute. IsByteOrdered** est **false**, les comparaisons d’ordre d’octet échouent.  
  
-   Un UDT défini dans une classe doit disposer d'un constructeur public qui n'accepte aucun argument. Vous pouvez éventuellement créer des constructeurs de classe surchargés supplémentaires.  
  
-   L'UDT doit dévoiler les éléments de données sous forme de champs publics ou de procédures de propriété.  
  
-   Les noms publics ne peuvent pas dépasser 128 caractères et doivent être conformes aux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] règles d’affectation de noms pour les identificateurs définis dans les [identificateurs de base de données](../../relational-databases/databases/database-identifiers.md).  
  
-   **sql_variant** colonnes ne peuvent pas contenir d’instances d’un type défini par l’utilisateur.  
  
-   Les membres hérités ne sont pas accessibles depuis [!INCLUDE[tsql](../../includes/tsql-md.md)] puisque le système de type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est pas compatible avec la hiérarchie d'héritage entre UDT. Toutefois, vous pouvez recourir à la fonction d'héritage au moment de structurer vos classes et pouvez appeler ces méthodes dans l'implémentation du code managé du type.  
  
-   Hormis le constructeur de classe, les membres ne peuvent pas être surchargés. Si vous créez une méthode surchargée, aucune erreur ne se produit au moment d'inscrire l'assembly ou de créer le type dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La détection de la méthode surchargée a lieu au moment de l'exécution et non lors de la création du type. Les méthodes surchargées peuvent exister dans la classe tant qu'elles ne sont jamais appelées. Une erreur est générée dès que vous appelez la méthode surchargée.  
  
-   Tous les membres **statiques** (ou **partagés**) doivent être déclarés comme constantes ou en lecture seule. Les membres statiques ne peuvent pas être mutables.  
  
-   Si le champ **SqlUserDefinedTypeAttribute. MaxByteSize** a la valeur-1, l’UDT sérialisé peut être aussi grand que la limite de taille d’objet volumineux (LOB) (actuellement 2 Go). La taille de l’UDT ne peut pas dépasser la valeur spécifiée dans le champ **MaxByteSized** .  
  
> [!NOTE]  
>  Bien qu’il ne soit pas utilisé par le serveur pour effectuer des comparaisons, vous pouvez éventuellement implémenter l’interface **System. IComparable** , qui expose une seule méthode, **CompareTo**. Elle intervient côté client dans des situations où il est préférable de comparer ou de classer avec précision des valeurs de type défini par l'utilisateur (UDT).  
  
## <a name="native-serialization"></a>Sérialisation native  
 Le choix du bon attribut de sérialisation pour votre UDT dépend du type d'UDT que vous essayez de créer. Le format de sérialisation **natif** utilise une structure très simple qui permet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à de stocker une représentation native efficace du type défini par l’utilisateur sur le disque. Le format **natif** est recommandé si l’UDT est simple et contient uniquement des champs des types suivants :  
  
 **bool**, **byte**, **sbyte**, **short**, **ushort**, **int**, **uint**, **long**, **ulong**, **float**, **double**, **SqlByte**, **SqlInt16**, **SqlInt32**, **SqlInt64**, **SqlDateTime**, **SqlSingle**, **SqlDouble**, **SqlMoney**, **SqlBoolean**  
  
 Les types de valeur qui sont composés de champs des types ci-dessus sont de bons candidats pour le format **natif** , tels que les **structs** en Visual C#, (ou les **structures** telles qu’elles sont connues dans Visual Basic). Par exemple, un UDT spécifié avec le format de sérialisation **natif** peut contenir un champ d’un autre UDT qui a également été spécifié avec le format **natif** . Si la définition de l’UDT est plus complexe et contient des types de données qui ne sont pas dans la liste ci-dessus, vous devez spécifier le format de sérialisation **UserDefined** à la place.  
  
 Le format **natif** présente les exigences suivantes :  
  
-   Le type ne doit pas spécifier de valeur pour **Microsoft. SqlServer. Server. SqlUserDefinedTypeAttribute. MaxByteSize**.  
  
-   Tous les champs doivent être sérialisables.  
  
-   **System. Runtime. InteropServices. StructLayoutAttribute** doit être spécifié comme **StructLayout. LAYOUTKINDSEQUENTIAL** si le type défini par l’utilisateur est défini dans une classe et non dans une structure. Cet attribut contrôle la disposition physique des champs de données et est utilisé pour contraindre les membres à se placer dans l'ordre dans lequel ils apparaissent. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise cet attribut pour déterminer l'ordre des champs des UDT au moyen de plusieurs valeurs.  
  
 Pour obtenir un exemple d’UDT défini avec la sérialisation **Native** , consultez le point défini par l' [utilisateur dans codage des types définis par l’utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md).  
  
## <a name="userdefined-serialization"></a>Sérialisation UserDefined  
 Le paramètre de format **UserDefined** pour l’attribut **Microsoft. SqlServer. Server. SqlUserDefinedTypeAttribute** donne au développeur un contrôle total sur le format binaire. Lorsque vous spécifiez la propriété de l’attribut **format** comme **UserDefined**, vous devez effectuer les opérations suivantes dans votre code :  
  
-   Spécifiez la propriété d’attribut **IsByteOrdered** facultative. La valeur par défaut est **false**.  
  
-   Spécifiez la propriété **MaxByteSize** de **Microsoft. SqlServer. Server. SqlUserDefinedTypeAttribute**.  
  
-   Écrivez du code pour implémenter les méthodes de **lecture** et d' **écriture** pour le type défini par l’utilisateur en implémentant l’interface **System. Data. Sql. IBinarySerialize** .  
  
 Pour obtenir un exemple d’UDT défini avec la sérialisation **UserDefined** , consultez l’UDT Currency dans [codage des types définis par l’utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md).  
  
> [!NOTE]  
>  Les champs UDT doivent utiliser la sérialisation native ou être persistants pour pouvoir être indexés.  
  
## <a name="serialization-attributes"></a>Attributs de sérialisation  
 Les attributs déterminent la façon dont la sérialisation est utilisée pour construire la représentation de stockage des types définis par l'utilisateur et pour transmettre des types définis par l'utilisateur par valeur au client. Vous devez spécifier **Microsoft. SqlServer. Server. SqlUserDefinedTypeAttribute** lors de la création de l’UDT. L’attribut **Microsoft. SqlServer. Server. SqlUserDefinedTypeAttribute** indique que la classe est un type défini par l’utilisateur (UDT) et spécifie le stockage pour le type défini par l’utilisateur. Vous pouvez éventuellement spécifier l’attribut **Serializable** , même si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne l’exige pas.  
  
 **Microsoft. SqlServer. Server. SqlUserDefinedTypeAttribute** a les propriétés suivantes.  
  
 **Format**  
 Spécifie le format de sérialisation, qui peut être **natif** ou **UserDefined**, en fonction des types de données du type défini par l’utilisateur (UDT).  
  
 **IsByteOrdered**  
 Valeur **booléenne** qui détermine comment [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effectue des comparaisons binaires sur le type défini par l’utilisateur.  
  
 **IsFixedLength**  
 Indique si toutes les instances de cet UDT ont la même longueur.  
  
 **MaxByteSize**  
 Taille maximale de l'instance, en octets. Vous devez spécifier **MaxByteSize** avec le format de sérialisation **UserDefined** . Pour un type défini par l’utilisateur avec la sérialisation définie par l’utilisateur spécifiée, **MaxByteSize** fait référence à la taille totale du type défini par l’utilisateur dans sa forme sérialisée, comme défini par l’utilisateur. La valeur de **MaxByteSize** doit être comprise entre 1 et 8000, ou définie sur-1 pour indiquer que le type défini par l’utilisateur est supérieur à 8000 octets (la taille totale ne peut pas dépasser la taille maximale de l’LOB). Imaginez un UDT avec une propriété d’une chaîne de 10 caractères (**System. Char**). Lorsque l'UDT est sérialisé à l'aide de BinaryWriter, la taille totale de la chaîne sérialisée est de 22 octets : 2 octets par caractère Unicode UTF-16, multipliés par le nombre maximal de caractères, plus 2 octets de contrôle de la charge mémoire générée par la sérialisation d'un flux binaire. Par conséquent, lors de la détermination de la valeur de **MaxByteSize**, la taille totale du type défini par l’utilisateur sérialisé doit être prise en compte : la taille des données sérialisées au format binaire plus la surcharge générée par la sérialisation.  
  
 **ValidationMethodName**  
 Nom de la méthode utilisée pour valider des instances du type défini par l'utilisateur.  
  
### <a name="setting-isbyteordered"></a>Définition de la propriété IsByteOrdered  
 Lorsque la propriété **Microsoft. SqlServer. Server. SqlUserDefinedTypeAttribute. IsByteOrdered** est définie sur **true**, vous garantissez que les données binaires sérialisées peuvent être utilisées pour le classement sémantique des informations. Par conséquent, chaque instance d'un objet UDT ordonné par octet peut avoir une seule représentation sérialisée. Lorsque vous soumettez les octets sérialisés à une comparaison dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les résultats doivent être les mêmes que si vous réalisiez cette opération de comparaison dans le code managé. Les fonctionnalités suivantes sont également prises en charge lorsque **IsByteOrdered** est défini sur **true**:  
  
-   Possibilité de créer des index dans les colonnes de ce type.  
  
-   Possibilité de créer des clés primaires et étrangères ainsi que des contraintes CHECK et UNIQUE dans les colonnes de ce type.  
  
-   Possibilité d'utiliser les clauses ORDER BY, GROUP BY et PARTITION BY de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Dans ces cas, la représentation binaire du type est utilisée pour déterminer l'ordre.  
  
-   Possibilité d'utiliser des opérateurs de comparaison dans des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   Possibilité de rendre persistantes des colonnes calculées de ce type.  
  
 Notez que les formats de sérialisation **natif** et **UserDefined** prennent en charge les opérateurs de comparaison suivants lorsque **IsByteOrdered** est défini sur **true**:  
  
-   Égal à (=)  
  
-   Différent de (!=)  
  
-   Supérieur à (>)  
  
-   Inférieur à (\<)  
  
-   Supérieur ou égal à (>=)  
  
-   Less than or equal to (&lt;=)  
  
### <a name="implementing-nullability"></a>Implémentation de la possibilité de valeur NULL  
 En plus de spécifier correctement les attributs de vos assemblys, votre classe doit également prendre en charge la possibilité de valeur NULL. Les UDT chargés dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prennent en charge la valeur null, mais pour que l’UDT puisse reconnaître une valeur null, la classe doit implémenter l’interface **INullable** . Pour plus d’informations et pour obtenir un exemple d’implémentation de la possibilité de valeur null dans un type défini par l’utilisateur, consultez [codage de types définis par l’utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md).  
  
### <a name="string-conversions"></a>Conversions de chaînes  
 Pour prendre en charge la conversion de chaînes vers et à partir du type défini par l’utilisateur, vous devez fournir une méthode **Parse** et une méthode **ToString** dans votre classe. La méthode **Parse** permet de convertir une chaîne en UDT. Elle doit être déclarée comme **static** (ou **shared** dans Visual Basic) et prendre un paramètre de type **System. Data. SqlTypes. SqlString**. Pour plus d’informations et pour obtenir un exemple de la façon d’implémenter les méthodes **Parse** et **ToString** , consultez [codage de types définis par l’utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md).  
  
## <a name="xml-serialization"></a>Sérialisation XML  
 Les UDT doivent prendre en charge la conversion vers et depuis le type de données **XML** en se conformant au contrat de sérialisation XML. **System.Xml. **L’espace de noms de sérialisation contient des classes utilisées pour sérialiser des objets en documents au format XML ou en flux. Vous pouvez choisir d’implémenter la sérialisation **XML** à l’aide de l’interface **IXmlSerializable** , qui fournit une mise en forme personnalisée pour la sérialisation et la désérialisation XML.  
  
 Outre les conversions explicites de UDT en **XML**, la sérialisation XML vous permet d’effectuer les opérations suivantes :  
  
-   Utilisez **XQuery** sur des valeurs d’instances UDT après conversion en type de données **XML** .  
  
-   Utiliser des UDT dans des requêtes paramétrables et des méthodes Web à l'aide des services Web XML natifs dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Utiliser des UDT pour recevoir un chargement en masse de données XML.  
  
-   Sérialiser des datasets contenant des tables avec des colonnes UDT.  
  
 Les UDT ne sont pas sérialisés dans les requêtes FOR XML. Pour exécuter une requête FOR XML qui affiche la sérialisation XML des UDT, convertissez explicitement chaque colonne UDT en type de données **XML** dans l’instruction SELECT. Vous pouvez également convertir explicitement les colonnes en **varbinary**, **varchar**ou **nvarchar**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un type défini par l’utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  
