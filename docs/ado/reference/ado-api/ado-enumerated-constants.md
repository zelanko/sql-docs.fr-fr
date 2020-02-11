---
title: Constantes énumérées ADO | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- enumerated constants [ADO]
ms.assetid: c97ed131-1a93-463c-9e61-22f029b0c474
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0a2b02498905b73f321d7585b5c91adfbfd1b4b4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67921020"
---
# <a name="ado-enumerated-constants"></a>Constantes énumérées ADO
Pour faciliter le débogage, les énumérations ADO répertorient une valeur pour chaque constante. Toutefois, cette valeur est purement indicative et peut passer d’une version d’ADO à une autre. Votre code ne doit dépendre que du nom, et non de la valeur réelle, de chaque constante énumérée.  
  
|||  
|-|-|  
|[ADCPROP_ASYNCTHREADPRIORITY_ENUM](../../../ado/reference/ado-api/adcprop-asyncthreadpriority-enum.md)|Pour un objet **Recordset** RDS, spécifie la priorité d’exécution du thread asynchrone qui récupère les données.|  
|[ADCPROP_AUTORECALC_ENUM](../../../ado/reference/ado-api/adcprop-autorecalc-enum.md)|Spécifie quand le fournisseur **MSDataShape** recalcule les colonnes agrégées et calculées dans un **jeu d’enregistrements**hiérarchique.|  
|[ADCPROP_UPDATECRITERIA_ENUM](../../../ado/reference/ado-api/adcprop-updatecriteria-enum.md)|Spécifie les champs qui peuvent être utilisés pour détecter les conflits pendant une mise à jour optimiste d’une ligne de la source de données avec un objet **Recordset** .|  
|[ADCPROP_UPDATERESYNC_ENUM](../../../ado/reference/ado-api/adcprop-updateresync-enum.md)|Spécifie si la méthode **UpdateBatch** est suivie d’une opération de méthode de **resynchronisation** implicite et, le cas échéant, de l’étendue de cette opération.|  
|[AffectEnum](../../../ado/reference/ado-api/affectenum.md)|Spécifie les enregistrements qui sont affectés par une opération.|  
|[BookmarkEnum](../../../ado/reference/ado-api/bookmarkenum.md)|Spécifie un signet qui indique où l’opération doit commencer.|  
|[CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)|Spécifie comment un argument de commande doit être interprété.|  
|[CompareEnum](../../../ado/reference/ado-api/compareenum.md)|Spécifie la position relative de deux enregistrements représentés par leurs signets.|  
|[ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md)|Spécifie les autorisations disponibles pour la modification des données dans une **connexion**, l’ouverture d’un **enregistrement**ou la spécification de valeurs pour la propriété **mode** des objets **Record** et **Stream** .|  
|[ConnectOptionEnum](../../../ado/reference/ado-api/connectoptionenum.md)|Spécifie si la méthode **Open** d’un objet **Connection** doit être retournée après (de façon synchrone) ou avant (de façon asynchrone) la connexion est établie.|  
|[ConnectPromptEnum](../../../ado/reference/ado-api/connectpromptenum.md)|Spécifie si une boîte de dialogue doit être affichée pour demander des paramètres manquants lors de l’ouverture d’une connexion à une source de données ODBC.|  
|[CopyRecordOptionsEnum](../../../ado/reference/ado-api/copyrecordoptionsenum.md)|Spécifie le comportement de la méthode **CopyRecord** .|  
|[CursorLocationEnum](../../../ado/reference/ado-api/cursorlocationenum.md)|Spécifie l’emplacement du moteur de curseur.|  
|[CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md)|Spécifie les fonctionnalités que la méthode de **prise en charge** doit tester.|  
|[CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md)|Spécifie le type de curseur utilisé dans un objet **Recordset** .|  
|[DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md)|Spécifie le type de données d’un **champ**, d’un **paramètre**ou d’une **propriété**.|  
|[EditModeEnum](../../../ado/reference/ado-api/editmodeenum.md)|Spécifie l’état de modification d’un enregistrement.|  
|[ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md)|Spécifie le type d’erreur d’exécution ADO.|  
|[EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md)|Spécifie la raison pour laquelle un événement a eu lieu.|  
|[EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)|Spécifie l’état actuel de l’exécution d’un événement.|  
|[ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md)|Spécifie comment un fournisseur doit exécuter une commande.|  
|[FieldEnum](../../../ado/reference/ado-api/fieldenum.md)|Spécifie les champs spéciaux référencés dans la collection **Fields** d’un objet **Record** .|  
|[FieldAttributeEnum](../../../ado/reference/ado-api/fieldattributeenum.md)|Spécifie un ou plusieurs attributs d’un objet de **champ** .|  
|[FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md)|Spécifie l’état d’un objet de **champ** .|  
|[FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md)|Spécifie le groupe d’enregistrements à filtrer à partir d’un **jeu d’enregistrements**.|  
|[GetRowsOptionEnum](../../../ado/reference/ado-api/getrowsoptionenum.md)|Spécifie le nombre d’enregistrements à récupérer à partir d’un **jeu d’enregistrements**.|  
|[IsolationLevelEnum](../../../ado/reference/ado-api/isolationlevelenum.md)|Spécifie le niveau d’isolation des transactions pour un objet de **connexion** .|  
|[LineSeparatorsEnum](../../../ado/reference/ado-api/lineseparatorsenum.md)|Spécifie le caractère utilisé comme séparateur de lignes dans les objets de **flux** de texte.|  
|[LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md)|Spécifie le type de verrou placé sur les enregistrements lors de la modification.|  
|[MarshalOptionsEnum](../../../ado/reference/ado-api/marshaloptionsenum.md)|Spécifie les enregistrements qui doivent être renvoyés au serveur.|  
|[MoveRecordOptionsEnum](../../../ado/reference/ado-api/moverecordoptionsenum.md)|Spécifie le comportement de la méthode **MoveRecord** de l’objet **Record** .|  
|[ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md)|Spécifie si un objet est ouvert ou fermé, s’il se connecte à une source de données, exécute une commande ou extrait des données.|  
|[ParameterAttributesEnum](../../../ado/reference/ado-api/parameterattributesenum.md)|Spécifie les attributs d’un objet de **paramètre** .|  
|[ParameterDirectionEnum](../../../ado/reference/ado-api/parameterdirectionenum.md)|Spécifie si le **paramètre** représente un paramètre d’entrée, un paramètre de sortie, ou les deux, ou si le paramètre est la valeur de retour d’une procédure stockée.|  
|[PersistFormatEnum](../../../ado/reference/ado-api/persistformatenum.md)|Spécifie le format d’enregistrement d’un **jeu d’enregistrements**.|  
|[PositionEnum](../../../ado/reference/ado-api/positionenum.md)|Spécifie la position actuelle du pointeur d’enregistrement dans un **Recordset**.|  
|[PropertyAttributesEnum](../../../ado/reference/ado-api/propertyattributesenum.md)|Spécifie les attributs d’un objet de **propriété** .|  
|[RecordCreateOptionsEnum](../../../ado/reference/ado-api/recordcreateoptionsenum.md)|Spécifie la méthode d' **ouverture** de l’objet d' **enregistrement** si un **enregistrement** existant doit être ouvert ou si un nouvel **enregistrement** doit être créé.|  
|[RecordOpenOptionsEnum](../../../ado/reference/ado-api/recordopenoptionsenum.md)|Spécifie les options d’ouverture d’un **enregistrement**. Ces valeurs peuvent être combinées à l’aide d’un opérateur OR.|  
|[RecordStatusEnum](../../../ado/reference/ado-api/recordstatusenum.md)|Spécifie l’état d’un enregistrement en ce qui concerne les mises à jour par lots et les autres opérations en bloc.|  
|[RecordTypeEnum](../../../ado/reference/ado-api/recordtypeenum.md)|Spécifie le type d’objet d' **enregistrement** .|  
|[ResyncEnum](../../../ado/reference/ado-api/resyncenum.md)|Spécifie si les valeurs sous-jacentes sont remplacées par un appel à **Resync**.|  
|[SaveOptionsEnum](../../../ado/reference/ado-api/saveoptionsenum.md)|Spécifie si un fichier doit être créé ou remplacé lors de l’enregistrement à partir d’un objet de **flux** . Les valeurs peuvent être combinées avec un opérateur AND.|  
|[SchemaEnum](../../../ado/reference/ado-api/schemaenum.md)|Spécifie le type de **jeu d’enregistrements** de schéma que la méthode **OpenSchema** récupère. Spécifie la direction d’une recherche d’enregistrement dans un **Recordset**.|  
|[SearchDirectionEnum](../../../ado/reference/ado-api/searchdirectionenum.md)|Spécifie la direction d’une recherche d’enregistrement dans un **Recordset**. Spécifie le type de **recherche** à exécuter.|  
|[SeekEnum](../../../ado/reference/ado-api/seekenum.md)|Spécifie le type de **recherche** à exécuter. Spécifie les options d’ouverture d’un objet de **flux** . Les valeurs peuvent être combinées avec un opérateur AND.|  
|[StreamOpenOptionsEnum](../../../ado/reference/ado-api/streamopenoptionsenum.md)|Spécifie les options d’ouverture d’un objet de **flux** . Les valeurs peuvent être combinées avec un opérateur AND. Spécifie si l’intégralité du flux ou la ligne suivante doit être lue à partir d’un objet de **flux** .|  
|[StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md)|Spécifie si l’intégralité du flux ou la ligne suivante doit être lue à partir d’un objet de **flux** . Spécifie le type de données stockées dans un objet de **flux** .|  
|[StreamTypeEnum](../../../ado/reference/ado-api/streamtypeenum.md)|Spécifie le type de données stockées dans un objet de **flux** . Spécifie si un séparateur de ligne est ajouté à la chaîne écrite dans un objet de **flux** .|  
|[StreamWriteEnum](../../../ado/reference/ado-api/streamwriteenum.md)|Spécifie si un séparateur de ligne est ajouté à la chaîne écrite dans un objet de **flux** . Spécifie le format lors de la récupération d’un **jeu d’enregistrements** sous forme de chaîne.|  
|[StringFormatEnum](../../../ado/reference/ado-api/stringformatenum.md)|Spécifie le format lors de la récupération d’un **jeu d’enregistrements** sous forme de chaîne. Spécifie les attributs de transaction d’un objet de **connexion** .|  
|[XactAttributeEnum](../../../ado/reference/ado-api/xactattributeenum.md)|Spécifie les attributs de transaction d’un objet de **connexion** .|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur l’API ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [Collections ADO](../../../ado/reference/ado-api/ado-collections.md)   
 [Propriétés dynamiques ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [Annexe B : erreurs ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [Événements ADO](../../../ado/reference/ado-api/ado-events.md)   
 [Méthodes ADO](../../../ado/reference/ado-api/ado-methods.md)   
 [Modèle objet ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Objets et interfaces ADO](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [Propriétés ADO](../../../ado/reference/ado-api/ado-properties.md)
