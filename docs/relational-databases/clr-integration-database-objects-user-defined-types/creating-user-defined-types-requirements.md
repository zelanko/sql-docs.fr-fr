---
title: Exigences de type définies par l’utilisateur (en anglais seulement) Microsoft Docs
description: Cet article décrit les décisions de conception importantes que vous devez prendre lorsque vous créez un UDT à installer sur SQL Server.
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
ms.openlocfilehash: 2b19a9179cba2225a2209255ce48220669e4bbef
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81486968"
---
# <a name="creating-user-defined-types---requirements"></a>Création de types définis par l’utilisateur - Exigences
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Vous devez prendre plusieurs décisions de conception importantes lors de la création [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]d’un type défini par l’utilisateur (UDT) à installer dans . Pour la plupart des types définis par l'utilisateur, il est recommandé de créer un type défini par l'utilisateur sous forme de structure mais il est également possible de le créer sous forme de classe. La définition de l'UDT doit être conforme aux spécifications de création d'UDT afin de pouvoir l'enregistrer avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="requirements-for-implementing-udts"></a>Configuration requise pour l'implémentation des types définis par l'utilisateur  
 Pour s'exécuter dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], votre UDT doit implémenter les éléments requis suivants dans sa définition :  
  
 L’UDT doit spécifier le **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute**. L’utilisation du **System.SerializableAttribute** est facultative, mais recommandée.  
  
-   L’UDT doit implémenter **l’interface System.Data.SqlTypes.INullable** dans la [!INCLUDE[msCoName](../../includes/msconame-md.md)] classe ou la structure en créant une méthode **statique** publique **(partagée** dans visual basic) **Null.** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est par défaut compatible avec la valeur NULL. Ceci est nécessaire pour que le code exécuté dans l'UDT puisse être en mesure de reconnaître une valeur NULL.  
  
-   L’UDT doit contenir une méthode de **parse** **statique** (ou **partagée)** publique qui prend en charge l’analyse de, et une méthode publique **ToString** pour la conversion en une représentation de chaîne de l’objet.  
  
-   Un UDT doté d’un format de sérialisation défini par l’utilisateur doit implémenter **l’interface System.Data.IBinarySerialize** et fournir une méthode **Lire** et **écrire.**  
  
-   L’UDT doit mettre en œuvre **System.Xml.Serialization.IXmlSerializable**, ou tous les champs publics et les propriétés doivent être de types qui sont XML sérialisable ou décoré avec l’attribut **XmlIgnore** si la sérialisation standard primordiale est nécessaire.  
  
-   Chaque objet UDT doit être soumis à une seule sérialisation. La validation échoue si les routines de sérialisation ou désérialisation reconnaissent plusieurs représentations d'un objet en particulier.  
  
-   **SqlUserDefinedTypeAttribute.IsByteOrdered** doit être **vrai** pour comparer les données dans l’ordre des byte. Si l’interface IComparable n’est pas implémentée et **SqlUserDefinedTypeAttribute.IsByteOrdered** est **faux,** les comparaisons d’ordres byte échoueront.  
  
-   Un UDT défini dans une classe doit disposer d'un constructeur public qui n'accepte aucun argument. Vous pouvez éventuellement créer des constructeurs de classe surchargés supplémentaires.  
  
-   L'UDT doit dévoiler les éléments de données sous forme de champs publics ou de procédures de propriété.  
  
-   Les noms publics ne peuvent pas être plus longs que 128 caractères, et doivent se conformer aux règles de nommage pour les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identificateurs tels que définis dans les [identifiants de base de données](../../relational-databases/databases/database-identifiers.md).  
  
-   **sql_variant** colonnes ne peuvent contenir des cas d’UDT.  
  
-   Les membres hérités ne sont pas accessibles depuis [!INCLUDE[tsql](../../includes/tsql-md.md)] puisque le système de type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est pas compatible avec la hiérarchie d'héritage entre UDT. Toutefois, vous pouvez recourir à la fonction d'héritage au moment de structurer vos classes et pouvez appeler ces méthodes dans l'implémentation du code managé du type.  
  
-   Hormis le constructeur de classe, les membres ne peuvent pas être surchargés. Si vous créez une méthode surchargée, aucune erreur ne se produit au moment d'inscrire l'assembly ou de créer le type dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La détection de la méthode surchargée a lieu au moment de l'exécution et non lors de la création du type. Les méthodes surchargées peuvent exister dans la classe tant qu'elles ne sont jamais appelées. Une erreur est générée dès que vous appelez la méthode surchargée.  
  
-   Tout membre **statique** (ou **partagé)** doit être déclaré comme constants ou comme lu seulement. Les membres statiques ne peuvent pas être mutables.  
  
-   Si le **champ SqlUserDefinedTypeAttribute.MaxByteSize** est réglé à -1, l’UDT sérialisé peut être aussi grand que la limite de taille grand objet (LOB) (actuellement 2 Go). La taille de l’UDT ne peut pas dépasser la valeur spécifiée dans le champ **MaxByteSized.**  
  
> [!NOTE]  
>  Bien qu’il ne soit pas utilisé par le serveur pour effectuer des comparaisons, vous pouvez implémenter optionnellement **l’interface System.IComparable,** qui expose une seule méthode, **CompareTo**. Elle intervient côté client dans des situations où il est préférable de comparer ou de classer avec précision des valeurs de type défini par l'utilisateur (UDT).  
  
## <a name="native-serialization"></a>Sérialisation native  
 Le choix du bon attribut de sérialisation pour votre UDT dépend du type d'UDT que vous essayez de créer. Le format de sérialisation **native** utilise [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] une structure très simple qui permet de stocker une représentation autochtone efficace de l’UDT sur disque. Le format **autochtone** est recommandé si l’UDT est simple et ne contient que les champs des types suivants :  
  
 **bool**, **byte**, **sbyte**, **short**, **ushort**, **int**, **uint**, **long**, **ulong**, **float**, **double**, **SqlByte**, **SqlInt16**, **SqlInt32**, **SqlInt64**, **SqlDateTime**, **SqlSingle**, **SqlDouble**, **SqlMoney**, **SqlBoolean**  
  
 Les types de valeur qui sont composés de champs des types ci-dessus sont de bons candidats pour le format **autochtone,** tels que **les structs** dans Visual C , (ou **Structures** comme ils sont connus dans Visual Basic). Par exemple, un UDT spécifié avec le format de sérialisation **autochtone** peut contenir un champ d’un autre UDT qui a également été spécifié avec le format **autochtone.** Si la définition UDT est plus complexe et contient des types de données qui ne sont pas sur la liste ci-dessus, vous devez spécifier le format de sérialisation **UserDefined** à la place.  
  
 Le format **Native** a les exigences suivantes :  
  
-   Le type ne doit pas spécifier une valeur pour **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.MaxByteSize**.  
  
-   Tous les champs doivent être sérialisables.  
  
-   Le **System.Runtime.InteropServices.StructLayoutAttribute** doit être spécifié comme **StructLayout.LayoutKindSequentiel** si l’UDT est défini dans une classe et non une structure. Cet attribut contrôle la disposition physique des champs de données et est utilisé pour contraindre les membres à se placer dans l'ordre dans lequel ils apparaissent. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise cet attribut pour déterminer l'ordre des champs des UDT au moyen de plusieurs valeurs.  
  
 Par exemple d’un UDT défini avec la sérialisation **autochtone,** voir le Point UDT dans [Coding User-Defined Types](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md).  
  
## <a name="userdefined-serialization"></a>Sérialisation UserDefined  
 Le paramètre format **UserDefined** pour l’attribut **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute** donne au développeur un contrôle total sur le format binaire. Lorsque vous spécifiez la propriété **d’attribut Format** en tant **qu’utilisateurdéfin,** vous devez faire ce qui suit dans votre code :  
  
-   Spécifier la propriété **d’attribut IsByteOrdered** en option. La valeur par défaut est **false**.  
  
-   Spécifier la propriété **MaxByteSize** de la **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute**.  
  
-   Rédiger du code pour implémenter les méthodes **de lecture** et **d’écriture** de l’UDT en implémentant **l’interface System.Data.Sql.IBinarySerialize.**  
  
 Par exemple d’un UDT défini avec la sérialisation **définie par l’utilisateur,** voir l’UDT de devise dans [les types définis par l’utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md)de codage .  
  
> [!NOTE]  
>  Les champs UDT doivent utiliser la sérialisation native ou être persistants pour pouvoir être indexés.  
  
## <a name="serialization-attributes"></a>Attributs de sérialisation  
 Les attributs déterminent la façon dont la sérialisation est utilisée pour construire la représentation de stockage des types définis par l'utilisateur et pour transmettre des types définis par l'utilisateur par valeur au client. Vous devez spécifier le **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute** lors de la création de l’UDT. **L’attribut Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute** indique que la classe est un UDT et spécifie le stockage de l’UDT. Vous pouvez spécifier l’attribut [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Serializable,** mais cela ne nécessite pas.  
  
 Le **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute** a les propriétés suivantes.  
  
 **Format**  
 Spécifie le format de sérialisation, qui peut être **native** ou **utilisateurDécréfié**, en fonction des types de données de l’UDT.  
  
 **IsByteOrdered**  
 Une valeur **Boolean** qui [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] détermine comment effectue des comparaisons binaires sur l’UDT.  
  
 **IsFixedLength**  
 Indique si toutes les instances de cet UDT ont la même longueur.  
  
 **MaxByteSize**  
 Taille maximale de l'instance, en octets. Vous devez spécifier **MaxByteSize** avec le format de sérialisation **UserDefined.** Pour un UDT avec une sérialisation définie par l’utilisateur spécifié, **MaxByteSize** se réfère à la taille totale de l’UDT dans sa forme sérialisée telle que définie par l’utilisateur. La valeur de **MaxByteSize** doit être de l’ordre de 1 à 8000, ou réglée à -1 pour indiquer que l’UDT est supérieur à 8000 octets (la taille totale ne peut pas dépasser la taille maximale lob). Considérez un UDT avec une propriété d’une chaîne de 10 caractères (**System.Char**). Lorsque l'UDT est sérialisé à l'aide de BinaryWriter, la taille totale de la chaîne sérialisée est de 22 octets : 2 octets par caractère Unicode UTF-16, multipliés par le nombre maximal de caractères, plus 2 octets de contrôle de la charge mémoire générée par la sérialisation d'un flux binaire. Par conséquent, lors de la détermination de la valeur de **MaxByteSize**, la taille totale de l’UDT sérialisé doit être considérée: la taille des données sérialisées sous forme binaire plus les frais généraux encourus par la sérialisation.  
  
 **ValidationMethodName**  
 Nom de la méthode utilisée pour valider des instances du type défini par l'utilisateur.  
  
### <a name="setting-isbyteordered"></a>Définition de la propriété IsByteOrdered  
 Lorsque la propriété **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.IsByteOrdered** est concrétisée, vous garantissez en effet que les données binaires sérialisées peuvent être utilisées pour la commande sémantique de l’information. **true** Par conséquent, chaque instance d'un objet UDT ordonné par octet peut avoir une seule représentation sérialisée. Lorsque vous soumettez les octets sérialisés à une comparaison dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les résultats doivent être les mêmes que si vous réalisiez cette opération de comparaison dans le code managé. Les fonctionnalités suivantes sont également prises en charge lorsque **IsByteOrdered** est configuré pour **vrai**:  
  
-   Possibilité de créer des index dans les colonnes de ce type.  
  
-   Possibilité de créer des clés primaires et étrangères ainsi que des contraintes CHECK et UNIQUE dans les colonnes de ce type.  
  
-   Possibilité d'utiliser les clauses ORDER BY, GROUP BY et PARTITION BY de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Dans ces cas, la représentation binaire du type est utilisée pour déterminer l'ordre.  
  
-   Possibilité d'utiliser des opérateurs de comparaison dans des instructions [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
-   Possibilité de rendre persistantes des colonnes calculées de ce type.  
  
 Notez que les formats **de** sérialisation Native et **UserDefined** prennent en charge les opérateurs de comparaison suivants **lorsqu’IsByteOrdered** est configuré comme **suit**:  
  
-   Égal à (=)  
  
-   Différent de (!=)  
  
-   Supérieur à (>)  
  
-   Inférieur à (\<)  
  
-   Supérieur ou égal à (>=)  
  
-   Less than or equal to (&lt;=)  
  
### <a name="implementing-nullability"></a>Implémentation de la possibilité de valeur NULL  
 En plus de spécifier correctement les attributs de vos assemblys, votre classe doit également prendre en charge la possibilité de valeur NULL. Les UDT [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] chargés sont nuls, mais pour que l’UDT reconnaisse une valeur nulle, la classe doit implémenter **l’interface INullable.** Pour plus d’informations et un exemple de la façon de mettre en œuvre la nullabilité dans un UDT, voir [Coding User-Defined Types](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md).  
  
### <a name="string-conversions"></a>Conversions de chaînes  
 Pour soutenir la conversion des cordes vers et depuis l’UDT, vous devez fournir une méthode **Parse** et une méthode **ToString** dans votre classe. La méthode **Parse** permet de convertir une chaîne en UDT. Il doit être déclaré **statique** (ou **partagé** dans Visual Basic), et prendre un paramètre de type **System.Data.SqlTypes.SqlString**. Pour plus d’informations et un exemple de la façon de mettre en œuvre les méthodes **Parse** et **ToString,** voir [Coding User-Defined Types](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md).  
  
## <a name="xml-serialization"></a>Sérialisation XML  
 Les UDT doivent prendre en charge la conversion vers et depuis le type de données **xml** en se conformant au contrat de sérialisation XML. L’espace de nom **System.Xml.Serialization** contient des classes qui sont utilisées pour sérialiser des objets dans des documents ou des flux de format XML. Vous pouvez choisir d’implémenter la sérialisation **xml** en utilisant l’interface **IXmlSerializable,** qui fournit un formatage personnalisé pour la sérialisation et la désétérialisation XML.  
  
 En plus d’effectuer des conversions explicites de l’UDT à **xml**, la sérialisation XML vous permet de :  
  
-   Utilisez **Xquery** sur les valeurs des instances UDT après la conversion au type de données **xml.**  
  
-   Utiliser des UDT dans des requêtes paramétrables et des méthodes Web à l'aide des services Web XML natifs dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Utiliser des UDT pour recevoir un chargement en masse de données XML.  
  
-   Sérialiser des datasets contenant des tables avec des colonnes UDT.  
  
 Les UDT ne sont pas sérialisés dans les requêtes FOR XML. Pour exécuter une requête FOR XML qui affiche la sérialisation XML des UDT, convertissez explicitement chaque colonne UDT au type de données **xml** dans la déclaration SELECT. Vous pouvez également convertir explicitement les colonnes en **varbinaire,** **varchar**, ou **nvarchar**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un type défini par l’utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  
