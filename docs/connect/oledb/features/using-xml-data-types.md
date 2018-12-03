---
title: À l’aide des Types de données XML | Microsoft Docs
description: À l’aide des Types de données XML avec OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- IRowsetChange interface
- IRowsetUpdate interface
- data access [OLE DB Driver for SQL Server], xml data type
- OLE DB Driver for SQL Server schema rowsets
- PROVIDER_TYPES rowset
- IColumnsInfo interface
- IRowsetFind interface
- IColumnsRowset interface
- PROCEDURE_PARAMETERS rowset
- MSOLEDBSQL, XML
- xml data type [SQL Server], OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server, XML
- IRowset interface
- ISequentialStream interface
- ISSCommandWithParameters interface
- SS_XMLSCHEMA rowset
- OLE DB Driver for SQL Server OLE DB interfaces
- XML [SQL Server], OLE DB Driver for SQL Server
- COLUMNS rowset
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 729d2f7288e6156cdd0688f6eed4b3e5acada5ff
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52391456"
---
# <a name="using-xml-data-types"></a>Utilisation de types de données XML
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] a introduit un type de données **xml** qui vous permet de stocker des documents et des fragments XML dans une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Le type de données **xml** est intégré dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et s’apparente à certains égards à d’autres types intégrés, comme **int** et **varchar**. Tout comme les autres types intégrés, vous pouvez utiliser le type de données **xml** en tant que type de colonne quand vous créez une table ou en tant que type de variable, type de paramètre ou type de retour de fonction ou bien dans des fonctions CAST et CONVERT.  
  
## <a name="programming-considerations"></a>Éléments de programmation à prendre en considération  
 XML peut être autodescriptif dans ce sens où il peut inclure un en-tête XML (facultatif) qui spécifie l'encodage du document. Par exemple :  
  
 `<?xml version="1.0" encoding="windows-1252"?><doc/>`  
  
 Le standard XML décrit la manière dont un processeur XML est capable de détecter l'encodage utilisé pour un document en examinant les premiers octets du document. Parfois, il est possible que l'encodage spécifié par l'application soit en conflit avec celui spécifié par le document. Dans le cadre des documents passés en tant que paramètres liés, XML est traité en tant que données binaires par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ; aucune conversion n'est donc réalisée et l'analyseur XML peut sans problème exploiter l'encodage spécifié dans le document. Toutefois, pour les données XML liées en tant que données de type WSTR, l'application doit alors garantir que le document est encodé au format Unicode. Ce scénario peut impliquer le chargement du document dans un DOM, le passage à l’encodage Unicode et la sérialisation du document. Sans cette étape, des conversions de données peuvent se produire et générer des données XML non valides ou endommagées.  
  
 Il existe également un risque potentiel de conflit lorsque vous spécifiez du XML dans des littéraux. Par exemple, les données suivantes ne sont pas valides :  
  
 `INSERT INTO xmltable(xmlcol) VALUES('<?xml version="1.0" encoding="UTF-16"?><doc/>')`  
  
 `INSERT INTO xmltable(xmlcol) VALUES(N'<?xml version="1.0" encoding="UTF-8"?><doc/>')`  
  
## <a name="ole-db-driver-for-sql-server"></a>OLE DB Driver pour SQL Server 
 DBTYPE_XML est un nouveau type de données au format XML dans le pilote OLE DB pour SQL Server. De plus, vous pouvez accéder aux données XML par le biais des types OLE DB existants DBTYPE_BYTES, DBTYPE_WSTR, DBTYPE_BSTR, DBTYPE_XML, DBTYPE_STR, DBTYPE_VARIANT et DBTYPE_IUNKNOWN. Les données stockées dans les colonnes de type XML peuvent être récupérées à partir d’une colonne d’un ensemble de lignes OLE DB Driver pour SQL Server dans les formats suivants :  
  
-   Chaîne de texte  
  
-   **ISequentialStream**  
  
> [!NOTE]  
>  OLE DB Driver pour SQL Server n’inclut pas de lecteur SAX, mais vous pouvez aisément passer l’interface **ISequentialStream** à des objets SAX et DOM dans MSXML.  
  
 **ISequentialStream** doit être utilisée pour la récupération de documents XML volumineux. Les mêmes techniques utilisées pour les types de valeur élevée s'appliquent également à XML. Pour plus d’informations, consultez [à l’aide des Types de valeur volumineux](../../oledb/features/using-large-value-types.md).  
  
 Les données stockées dans les colonnes de type XML dans un ensemble de lignes peuvent également être récupérées, insérées ou mises à jour par une application via les interfaces classiques, comme **IRow::GetColumns**, **IRowChange::SetColumns** et **ICommand::Execute**. De la même façon que pour la récupération, une application peut passer une chaîne de texte ou une interface **ISequentialStream** à OLE DB Driver pour SQL Server.  
  
> [!NOTE]  
>  Pour envoyer des données XML dans un format de chaîne par le biais de l’interface **ISequentialStream**, vous devez obtenir **ISequentialStream** en spécifiant DBTYPE_IUNKNOWN et affecter la valeur Null à son argument *pObject* dans la liaison.  
  
 Lorsque des données XML extraites apparaissent tronquées en raison d'une mémoire tampon du consommateur trop petite, la longueur retournée peut être 0xffffffff, ce qui signifie qu'elle est n'est pas connue. Ce comportement est cohérent avec son implémentation en tant que type de données transmis au client sans envoyer des informations de longueur avant les données réelles. Dans certains cas, la longueur réelle peut être retournée quand le fournisseur a mis en mémoire tampon la valeur tout entière (par exemple, **IRowset::GetData**) et dans le cadre d’une conversion des données.  
  
 Les données XML envoyées à SQL Server sont traitées en tant que données binaires par le serveur. Ce comportement empêche tout risque de conversion et permet à l’analyseur XML de détecter automatiquement l’encodage XML. Un plus large éventail de documents XML (par exemple, les documents encodés au format UTF-8) peuvent être acceptés en tant qu'entrées dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Si du contenu XML d'entrée est lié en tant que données du type DBTYPE_WSTR, l'application doit garantir qu'il est déjà encodé en Unicode pour éviter tout risque d'altération suite à des conversions de données indésirables.  
  
### <a name="data-bindings-and-coercions"></a>Liaisons de données et forçages de type  
 Le tableau suivant décrit la liaison et le forçage de type survenant quand vous utilisez les types de données répertoriés avec le type de données **xml** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
|Type de données|Vers le serveur<br /><br /> **XML**|Vers le serveur<br /><br /> **Non-XML**|Depuis le serveur<br /><br /> **XML**|Depuis le serveur<br /><br /> **Non-XML**|  
|---------------|---------------------------|--------------------------------|-----------------------------|----------------------------------|  
|DBTYPE_XML|Transfert direct<sup>6,7</sup>|Erreur<sup>1</sup>|OK<sup>11, 6</sup>|Erreur<sup>8</sup>|  
|DBTYPE_BYTES|Transfert direct<sup>6,7</sup>|N/A<sup>2</sup>|OK <sup>11, 6</sup>|N/A <sup>2</sup>|  
|DBTYPE_WSTR|Transfert direct<sup>6,10</sup>|N/A <sup>2</sup>|OK<sup>4, 6, 12</sup>|N/A <sup>2</sup>|  
|DBTYPE_BSTR|Transfert direct<sup>6,10</sup>|N/A <sup>2</sup>|OK <sup>3</sup>|N/A <sup>2</sup>|  
|DBTYPE_STR|OK<sup>6, 9, 10</sup>|N/A <sup>2</sup>|OK<sup>5, 6, 12</sup>|N/A <sup>2</sup>|  
|DBTYPE_IUNKNOWN|Flux d’octets via **ISequentialStream**<sup>7</sup>|N/A <sup>2</sup>|Flux d’octets via **ISequentialStream**<sup>11</sup>|N/A <sup>2</sup>|  
|DBTYPE_VARIANT (VT_UI1 &#124; VT_ARRAY)|Transfert direct<sup>6,7</sup>|N/A <sup>2</sup>|Néant|N/A <sup>2</sup>|  
|DBTYPE_VARIANT (VT_BSTR)|Transfert direct<sup>6,10</sup>|N/A <sup>2</sup>|OK<sup>3</sup>|N/A <sup>2</sup>|  
  
 <sup>1</sup>Si un type de serveur autre que DBTYPE_XML est spécifié avec **ICommandWithParameters::SetParameterInfo** et si le type d’accesseur est DBTYPE_XML, une erreur se produit lors de l’exécution de l’instruction (DB_E_ERRORSOCCURRED, l’état du paramètre est DBSTATUS_E_BADACCESSOR) ; sinon, les données sont envoyées au serveur, mais celui-ci retourne une erreur indiquant qu’aucune conversion implicite de XML vers le type de données du paramètre n’a lieu.  
  
 <sup>2</sup>Non traité dans cet article.  
  
 <sup>3</sup>Le format est UTF-16. Absence de marque d’ordre d’octet (BOM), de spécification d’encodage et de marque de fin Null.  
  
 <sup>4</sup>Le format est UTF-16. Absence de marque d’ordre d’octet (BOM), de spécification d’encodage et de marque de fin Null.  
  
 <sup>5</sup>Le format employé est celui de caractères multioctets encodés dans la page de codes du client avec une marque de fin Null. Toute conversion à partir de code Unicode sur le serveur risque d’endommager les données. Cette liaison est donc déconseillée.  
  
 <sup>6</sup>BY_REF peut être utilisé.  
  
 <sup>7</sup>Les données UTF-16 doivent commencer par une marque d’ordre d’octet. Si cela n'est pas le cas, il est possible que l'encodage ne soit pas correctement reconnu par le serveur.  
  
 <sup>8</sup>La validation peut avoir lieu au moment de créer l’accesseur ou au moment de l’extraction. L'erreur est DB_E_ERRORSOCCURRED et l'état de la liaison est défini sur DBBINDSTATUS_UNSUPPORTEDCONVERSION.  
  
 <sup>9</sup>Les données sont converties au format Unicode à l’aide de la page de codes du client avant d’être envoyées au serveur. Si l’encodage du document ne correspond pas à la page de codes du client, les données risquent d’être endommagées. Cette liaison est donc fortement déconseillée.  
  
 <sup>10</sup>Une marque d’ordre d’octet est toujours ajoutée aux données envoyées au serveur. Si les données commencent déjà par une marque d’ordre d’octet, deux marques d’ordre d’octet apparaissent alors au démarrage de la mémoire tampon. Le serveur utilise la première marque d’ordre d’octet pour reconnaître l’encodage en tant qu’encodage UTF-16, puis l’ignore. La deuxième marque d'ordre d'octet est interprétée comme un espace insécable de largeur nulle.  
  
 <sup>11</sup>Le format est UTF-16. Absence de spécification d’encodage et ajout d’une marque d’ordre d’octet aux données reçues du serveur. Si le serveur retourne une chaîne vide, une marque d’ordre d’octet est quand même retournée à l’application. Si la longueur de la mémoire tampon est un nombre impair d’octets, les données sont tronquées comme il se doit. Si la valeur entière est retournée en plusieurs segments, vous pouvez les concaténer pour reconstituer la valeur correcte.  
  
 <sup>12</sup>Si la longueur de la mémoire tampon affiche moins de deux caractères, soit un espace insuffisant pour la marque de fin Null, une erreur de dépassement de capacité est signalée.  
  
> [!NOTE]  
>  Aucune donnée n'est retournée pour les valeurs XML NULL.  
  
 Le standard XML exigent que les données XML encodées UTF-16 commencent par une marque d'ordre d'octet (BOM), soit le code de caractère UTF-16 0xFEFF. Quand vous utilisez des liaisons WSTR et BSTR, OLE DB Driver pour SQL Server n’exige pas ou n’ajoute pas de marque d’ordre d’octet puisque l’encodage provient implicitement de la liaison. Dans le cadre des liaisons BYTES, XML ou IUNKNOWN, l'objectif recherché est la simplification de l'utilisation d'autres processeurs et systèmes de stockage XML. Dans ce cas, une marque d’ordre d’octet doit être présente avec les données XML encodées UTF-16 et l’application n’a pas à se soucier de l’encodage réel puisque la majorité des processeurs XML (dont SQL Server) détectent l’encodage par inspection des premiers octets de la valeur. Les données XML reçues d’OLE DB Driver pour SQL Server au moyen des liaisons BYTES, XML ou IUNKNOWN sont toujours encodées au format UTF-16 avec une marque d’ordre d’octet et sans déclaration d’encodage incorporée.  
  
 Les conversions de données fournies par les services principaux OLE DB (**IDataConvert**) ne s’appliquent pas à DBTYPE_XML.  
  
 La validation s'effectue lorsque les données sont envoyées au serveur. Validation côté client et l’encodage des modifications doivent être gérés par votre application. Il est recommandé que vous ne pas traiter les données XML directement, mais utilisez plutôt un lecteur DOM ou SAX pour le traiter.  
  
 Les types DBTYPE_NULL et DBTYPE_EMPTY peuvent être liés pour des paramètres d'entrée mais pas pour des paramètres de résultats ou pour des sorties. S'ils sont liés pour des paramètres d'entrée, l'état doit être défini sur DBSTATUS_S_ISNULL ou DBSTATUS_S_DEFAULT.  
  
 DBTYPE_XML peut être converti en DBTYPE_EMPTY et DBTYPE_NULL, DBTYPE_EMPTY peut être converti en DBTYPE_XML mais DBTYPE_NULL ne peut pas être converti en DBTYPE_XML, ce qui est cohérent avec DBTYPE_WSTR.  
  
 DBTYPE_IUNKNOWN est une liaison prise en charge (voir le tableau précédent), mais il n’existe aucune conversion entre DBTYPE_XML et DBTYPE_IUNKNOWN. DBTYPE_IUNKNOWN ne peut pas être utilisé avec DBTYPE_BYREF.  
  
### <a name="ole-db-rowset-additions-and-changes"></a>Ajout et modifications dans les ensembles de lignes OLE DB  
 OLE DB Driver pour SQL Server ajoute de nouvelles valeurs ou modifie à la plupart des principaux ensembles de lignes de schéma OLE DB.  
  
#### <a name="the-columns-and-procedureparameters-schema-rowsets"></a>Ensembles de lignes de schéma COLUMNS et PROCEDURE_PARAMETERS  
 Les ajouts réalisés dans les ensembles de lignes de schéma COLUMNS et PROCEDURE_PARAMETERS incluent les colonnes suivantes :  
  
|Nom de colonne|Type|Description|  
|-----------------|----------|-----------------|  
|SS_XML_SCHEMACOLLECTION_CATALOGNAME|DBTYPE_WSTR|Nom d'un catalogue dans lequel une collection de schémas XML est définie. Null pour une colonne non-XML ou une colonne XML non typée.|  
|SS_XML_SCHEMACOLLECTION_SCHEMANAME|DBTYPE_WSTR|Nom d'un schéma dans lequel une collection de schémas XML est définie. Null pour une colonne non-XML ou une colonne XML non typée.|  
|SS_XML_SCHEMACOLLECTIONNAME|DBTYPE_WSTR|Nom de la collection de schémas XML. Null pour une colonne non-XML ou une colonne XML non typée.|  
  
#### <a name="the-providertypes-schema-rowset"></a>Ensemble de lignes de schéma PROVIDER_TYPES  
 Dans l’ensemble de lignes de schéma PROVIDER_TYPES, la valeur COLUMN_SIZE est 0 pour le type de données **xml** et la valeur DATA_TYPE est DBTYPE_XML.  
  
#### <a name="the-ssxmlschema-schema-rowset"></a>Ensemble de lignes de schéma SS_XMLSCHEMA  
 Un nouvel ensemble de lignes de schéma SS_XMLSCHEMA permettant d'extraire des informations de schéma XML est proposé pour les clients. L’ensemble de lignes SS_XMLSCHEMA contient les colonnes suivantes :  
  
|Nom de colonne|Type|Description|  
|-----------------|----------|-----------------|  
|SCHEMACOLLECTION_CATALOGNAME|DBTYPE_WSTR|Catalogue auquel une collection XML appartient.|  
|SCHEMACOLLECTION_SCHEMANAME|DBTYPE_WSTR|Schéma auquel une collection XML appartient.|  
|SCHEMACOLLECTIONNAME|DBTYPE_WSTR|Nom d’une collection de schémas XML pour les colonnes XML typées, valeur Null dans le cas contraire.|  
|TARGETNAMESPACEURI|DBTYPE_WSTR|Espace de noms cible d'un schéma XML.|  
|SCHEMACONTENT|DBTYPE_WSTR|Contenu du schéma XML.|  
  
 L'étendue de chaque schéma XML est définie par nom de catalogue, nom de schéma, nom de collection de schémas et par URI (Uniform Resource Identifier) d'espace de noms cible. Qui plus est, un nouveau GUID nommé DBSCHEMA_XML_COLLECTIONS est également défini. Le nombre de restrictions et les colonnes restreintes pour l'ensemble de lignes de schéma SS_XMLSCHEMA sont définis comme suit.  
  
|GUID|Nombre de restrictions|Colonnes restreintes|  
|----------|----------------------------|------------------------|  
|DBSCHEMA_XML_COLLECTIONS|4|SCHEMACOLLECTION_CATALOGNAME<br /><br /> SCHEMACOLLECTION_SCHEMANAME<br /><br /> SCHEMACOLLECTIONNAME<br /><br /> TARGETNAMESPACEURI|  
  
### <a name="ole-db-property-set-additions-and-changes"></a>Ajouts et modifications effectués dans le jeu de propriétés OLE DB  
 OLE DB Driver pour SQL Server ajoute de nouvelles valeurs ou modifie à la plupart de la propriété OLE DB core jeux.  
  
#### <a name="the-dbpropsetsqlserverparameter-property-set"></a>Jeu de propriétés DBPROPSET_SQLSERVERPARAMETER  
 Pour permettre la prise en charge du type de données **xml** via OLE DB, OLE DB Driver pour SQL Server implémente le nouveau jeu de propriétés DBPROPSET_SQLSERVERPARAMETER qui contient les valeurs suivantes.  
  
|Nom   |Type|Description|  
|----------|----------|-----------------|  
|SSPROP_PARAM_XML_SCHEMACOLLECTION_CATALOGNAME|DBTYPE_WSTR|Nom d'un catalogue (base de données) dans lequel une collection de schémas XML est définie. Une des trois parties qui composent l’identificateur de nom SQL.|  
|SSPROP_PARAM_XML_SCHEMACOLLECTION_SCHEMANAME|DBTYPE_WSTR|Nom d'un schéma XML dans la collection de schémas. Une des trois parties qui composent l'identificateur de nom SQL.|  
|SSPROP_PARAM_XML_SCHEMACOLLECTIONNAME|DBTYPE_WSTR|Nom de la collection de schémas XML dans le catalogue. Une des trois parties qui composent l'identificateur de nom SQL.|  
  
#### <a name="the-dbpropsetsqlservercolumn-property-set"></a>Jeu de propriétés DBPROPSET_SQLSERVERCOLUMN  
 Pour prendre en charge la création de tables dans l’interface **ITableDefinition**, OLE DB Driver pour SQL Server ajoute trois nouvelles colonnes au jeu de propriétés DBPROPSET_SQLSERVERCOLUMN.  
  
|Nom   |Type|Description|  
|----------|----------|-----------------|  
|SSPROP_COL_XML_SCHEMACOLLECTION_CATALOGNAME|VT_BSTR|Pour les colonnes XML typées, cette propriété est une chaîne qui spécifie le nom du catalogue où le schéma XML est stocké. Pour les autres types de colonnes, cette propriété retourne une chaîne vide.|  
|SSPROP_COL_XML_SCHEMACOLLECTION_SCHEMANAME|VT_BSTR|Pour les colonnes XML typées, cette propriété est une chaîne qui spécifie le nom de schéma XML qui définit cette colonne.|  
|SSPROP_COL_XML_SCHEMACOLLECTIONNAME|VT_BSTR|Pour les colonnes XML typées, cette propriété est une chaîne qui spécifie le nom de la collection de schémas XML qui définit la valeur.|  
  
 De même que les valeurs SSPROP_PARAM, toutes ces propriétés sont facultatives et sont vides par défaut. Les valeurs SSPROP_COL_XML_SCHEMACOLLECTION_CATALOGNAME et SSPROP_COL_XML_SCHEMACOLLECTION_SCHEMANAME peuvent être spécifiées uniquement si la valeur SSPROP_COL_XML_SCHEMACOLLECTIONNAME est spécifiée. Lorsque vous passez des données XML au serveur, si ces valeurs sont incluses, leur raison d'être (validité) est vérifiée par rapport à la base de données actuelle et les données d'instance sont vérifiées par rapport au schéma. Dans tous les cas, pour être valides, elles doivent toutes être vides ou renseignées.  
  
### <a name="ole-db-interface-additions-and-changes"></a>Ajout et modifications dans l'interface OLE DB  
 OLE DB Driver pour SQL Server ajoute de nouvelles valeurs ou modifie à la plupart des principales qu'interfaces OLE DB.  
  
#### <a name="the-isscommandwithparameters-interface"></a>Interface ISSCommandWithParameters  
 Pour permettre la prise en charge du type de données **xml** via OLE DB, OLE DB Driver pour SQL Server implémente plusieurs modifications, notamment l’ajout de l’interface [ISSCommandWithParameters](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md). Cette nouvelle interface hérite de l’interface OLE DB **ICommandWithParameters** principale. Outre les trois méthodes héritées **d’ICommandWithParameters** (**GetParameterInfo**, **MapParameterNames** et **SetParameterInfo**), **ISSCommandWithParameters** fournit les méthodes [GetParameterProperties](../../oledb/ole-db-interfaces/isscommandwithparameters-getparameterproperties-ole-db.md) et [SetParameterProperties](../../oledb/ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md) employées pour la gestion des types de données spécifiques au serveur.  
  
> [!NOTE]  
>  L’interface **ISSCommandWithParameters** exploite également la nouvelle structure SSPARAMPROPS.  
  
#### <a name="the-icolumnsrowset-interface"></a>Interface IColumnsRowset  
 OLE DB Driver pour SQL Server ajoute les colonnes spécifiques à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]suivantes à l’ensemble de lignes retourné par la méthode **IColumnRowset::GetColumnsRowset**. Ces colonnes contiennent le nom en trois parties d'une collection de schémas XML. Dans le cas des colonnes non XML ou des colonnes XML non typées, ces trois colonnes possèdent toutes la valeur NULL par défaut.  
  
|Nom de colonne|Type|Description|  
|-----------------|----------|-----------------|  
|DBCOLUMN_SS_XML_SCHEMACOLLECTION_CATALOGNAME|DBTYPE_WSTR|Catalogue auquel une collection de schémas XML appartient.<br /><br /> Possède la valeur NULL sinon.|  
|DBCOLUMN_SS_XML_SCHEMACOLLECTION_SCHEMANAME|DBTYPE_WSTR|Schéma auquel une collection de schémas XML appartient. Possède la valeur NULL sinon.|  
|DBCOLUMN_SS_XML_SCHEMACOLLECTIONNAME|DBTYPE_WSTR|Nom d'une collection de schémas XML pour les colonnes XML typées, valeur NULL dans le cas contraire.|  
  
#### <a name="the-irowset-interface"></a>Interface IRowset  
 Une instance XML est récupérée d’une colonne XML au moyen de la méthode **IRowset::GetData**. En fonction de la liaison spécifiée par le client, une instance XML peut être extraite en tant que type DBTYPE_BSTR, DBTYPE_WSTR, DBTYPE_VARIANT, DBTYPE_XML, DBTYPE_STR ou DBTYPE_BYTES, ou bien en tant qu'interface via DBTYPE_IUNKNOWN. Si le consommateur spécifie DBTYPE_BSTR, DBTYPE_WSTR ou DBTYPE_VARIANT, le fournisseur convertit l'instance XML d'après le type demandé par l'utilisateur et le stocke à l'emplacement précisé dans la liaison correspondante.  
  
 Si le consommateur spécifie DBTYPE_IUNKNOWN et affecte la valeur Null à l’argument *pObject*, ou affecte IID_ISequentialStream à l’argument *pObject*, le fournisseur retourne une interface **ISequentialStream** au consommateur afin que ce dernier puisse extraire les données XML de la colonne. **ISequentialStream** retourne ensuite les données XML sous forme de flux de caractères Unicode.  
  
 Au moment de retourner une valeur XML liée à DBTYPE_IUNKNOWN, le fournisseur signale une valeur de taille `sizeof (IUnknown *)`. Ce comportement est cohérent avec l’approche adoptée quand une colonne est liée en tant que DBTYPE_IUnknown ou DBTYPE_IDISPATCH et par DBTYPE_IUNKNOWN/ISequentialStream lorsque la taille de colonne exacte est impossible à déterminer.  
  
#### <a name="the-irowsetchange-interface"></a>Interface IRowsetChange  
 Il existe deux moyens pour un consommateur de mettre à jour une instance XML dans une colonne. Le premier est de faire appel à l’objet de stockage **ISequentialStream** créé par le fournisseur. Le consommateur peut appeler la méthode **ISequentialStream::Write** pour mettre à jour directement l’instance XML retournée par le fournisseur.  
  
 La deuxième approche repose sur la méthode **IRowsetChange::SetData** ou **IRowsetChange::InsertRow**. Dans ce cas précis, une instance XML issue de la mémoire tampon du consommateur peut être spécifiée dans une liaison de type DBTYPE_BSTR, DBTYPE_WSTR, DBTYPE_VARIANT, DBTYPE_XML ou DBTYPE_IUNKNOWN.  
  
 Si le type DBTYPE_BSTR, DBTYPE_WSTR ou DBTYPE_VARIANT est spécifié, le fournisseur stocke l’instance XML résidant dans la mémoire tampon du consommateur à l’intérieur de la colonne appropriée.  
  
 Si DBTYPE_IUNKNOWN/ISequentialStream est spécifié et que le consommateur ne spécifie aucun objet de stockage, il doit créer un objet **ISequentialStream** au préalable, lier le document XML à l’objet, puis passer l’objet au fournisseur par le biais de la méthode **IRowsetChange::SetData**. Le consommateur peut également créer un objet de stockage, affecter IID_ISequentialStream à l’argument pObject, créer un objet **ISequentialStream**, puis passer l’objet **ISequentialStream** à la méthode **IRowsetChange::SetData**. Dans les deux cas, le fournisseur peut récupérer l’objet XML via l’objet **ISequentialStream** et l’insérer dans une colonne appropriée.  
  
#### <a name="the-irowsetupdate-interface"></a>Interface IRowsetUpdate  
 L’interface **IRowsetUpdate** fournit les fonctionnalités nécessaires dans le cas de mises à jour différées. Les données mises à la disposition des ensembles de lignes ne sont pas disponibles pour d’autres transactions jusqu’à ce que le consommateur appelle la méthode **IRowsetUpdate::Update**.  
  
#### <a name="the-irowsetfind-interface"></a>Interface IRowsetFind  
 La méthode **IRowsetFind::FindNextRow** ne fonctionne pas avec le type de données **xml**. Quand vous appelez **IRowsetFind::FindNextRow** et que l’argument *hAccessor* spécifie une colonne de type DBTYPE_XML, la valeur DB_E_BADBINDINFO est retournée. Cette situation se produit quel que soit le type de colonne recherché. Pour tous les autres types de liaisons, la méthode **FindNextRow** échoue avec DB_E_BADCOMPAREOP si la colonne dans laquelle effectuer la recherche affiche le type de données **xml**.  
 
  
## <a name="see-also"></a> Voir aussi  
 [Fonctionnalités OLE DB Driver pour SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)    
 [ISSCommandWithParameters &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
