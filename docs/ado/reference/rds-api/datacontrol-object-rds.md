---
title: DataControl, objet (RDS) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- DataControl
- RDS.DataControl
helpviewer_keywords:
- DataControl object [ADO]
ms.assetid: d85ea4fc-451c-436e-97b8-58f92b149dd0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aa05b8b4be3c155c7ca59132892e0863dda60a5f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63134413"
---
# <a name="datacontrol-object-rds"></a>DataControl, objet (RDS)
Lie une requête de données [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) à un ou plusieurs contrôles (par exemple, une zone de texte, contrôle de grille ou zone de liste déroulante) pour afficher le **Recordset** données sur une page Web.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" ID="DataControl"  
   <PARAM NAME="Connect" VALUE="DSN=DSNName;UID=MyUserID;PWD=MyPassword;">  
   <PARAM NAME="Server" VALUE="https://awebsrvr">  
   <PARAM NAME="SQL" VALUE="QueryText">  
</OBJECT>  
```  
  
## <a name="remarks"></a>Notes  
 L’ID de classe pour le **RDS. DataControl** objet est 0-983A-00C04FC29E33 BD96C556 65A3 - 11 D.  
  
> [!NOTE]
>  Si vous obtenez une erreur un [RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) ou **RDS. DataControl** objet charger, assurez-vous que vous utilisez l’ID de classe approprié. La classe les identificateurs de ces objets ont changé depuis la version 1.0 et 1.1. En outre, n’oubliez pas que les colonnes nullables même doivent être définies lorsque vous utilisez le **RDS DataControl** objet.  
  
 Pour un scénario de base, vous devez définir uniquement les **SQL**, **Connect**, et **Server** propriétés de la **RDS. DataControl** objet, qui appelle automatiquement l’objet métier par défaut, [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md).  
  
 Toutes les propriétés dans le **RDS. DataControl** sont facultatifs, car les objets métier personnalisés peuvent remplacer leurs fonctionnalités.  
  
> [!NOTE]
>  Si vous interrogez plusieurs résultats, seul le premier [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) est retourné. Si plusieurs jeux de résultats est nécessaires, affectez chacun à sa propre **DataControl**. Un exemple d’une requête pour plusieurs résultats pourrait être la suivante : `"Select * from Authors, Select * from Topics"`  
  
 Ajout de « DFMode = 20 ; » à votre chaîne de connexion lorsque vous utilisez le **RDS. DataControl** objet peut améliorer les performances de votre serveur lorsque vous mettez à jour des données. Avec ce paramètre, le **RDSServer.DataFactory** objet sur le serveur utilise un mode moins gourmandes en ressources. Toutefois, les fonctionnalités suivantes ne sont pas disponibles dans cette configuration :  
  
-   À l’aide de requêtes paramétrables.  
  
-   Obtention d’informations de paramètre ou une colonne avant d’appeler le **Execute** (méthode).  
  
-   Paramètre **Transact mises à jour** à **True**.  
  
-   Obtention de l’état de la ligne.  
  
-   Appel de la [Resync](../../../ado/reference/ado-api/resync-method.md) (méthode).  
  
-   Actualisation (explicite ou automatique) via la [Update Resync](../../../ado/reference/ado-api/update-resync-property-dynamic-ado.md) propriété.  
  
-   Paramètre **commande** ou [Recordset](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md) propriétés.  
  
-   À l’aide de **adCmdTableDirect**.  
  
 Le **RDS. DataControl** objet s’exécute en mode asynchrone par défaut. Si vous avez besoin de l’exécution synchrone pour votre application, définissez la [ExecuteOptions](../../../ado/reference/rds-api/executeoptions-property-rds.md) paramètre égal à **est adcExecSync** et [FetchOptions](../../../ado/reference/rds-api/fetchoptions-property-rds.md) paramètre égal à **valeur adcFetchUpFront**, comme illustré dans l’exemple suivant.  
  
```  
<OBJECT CLASSID="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"   
    ID="DataControl"  
   <PARAM NAME="Connect" VALUE="DSN=DSNName;UID=MyUserID;PWD=MyPassword;">  
   <PARAM NAME="Server" VALUE="https://awebsrvr">  
   <PARAM NAME="SQL" VALUE="QueryText">  
   <PARAM NAME="ExecuteOptions" VALUE="1">   <PARAM NAME="FetchOptions" VALUE="1">  
</OBJECT>  
```  
  
 Utilisez une **RDS. DataControl** objet pour lier les résultats d’une requête unique à un ou plusieurs contrôles visuels. Par exemple, supposons que vous codez une requête demandant des données client, nom de résidence, lieu de naissance, âge et statut de client de priorité. Vous pouvez utiliser un seul **RDS. DataControl** objet pour afficher le nom d’un client, l’âge et la région dans trois zones de texte distinct ; Statut de client de priorité dans une case à cocher ; et toutes les données dans un contrôle de grille.  
  
 Utilisez différents **RDS. DataControl** objets pour lier les résultats de plusieurs requêtes à différents contrôles visuels. Par exemple, supposons que vous utilisez une requête pour obtenir des informations sur un client et une deuxième requête pour obtenir des informations sur les produits achetés par le client. Vous souhaitez afficher les résultats de la première requête dans trois zones de texte et une case à cocher et les résultats de la deuxième requête dans un contrôle de grille. Si vous utilisez l’objet métier par défaut (**RDSServer.DataFactory**), vous devez procédez comme suit :  
  
-   Ajoutez deux **RDS. DataControl** objets à votre page Web.  
  
-   Écriture de deux requêtes, une pour chaque **SQL** propriété des deux **RDS. DataControl** objets. Un seul **RDS. DataControl** objet contiendra une requête SQL demandant des informations client ; la seconde contiendra une requête demandant une liste d’articles achetés par le client.  
  
-   Dans les balises d’objet de chaque contrôle lié, spécifiez la valeur DATAFLD pour définir les valeurs pour les données que vous souhaitez afficher dans chaque contrôle visuel.  
  
 Il n’existe aucune restriction de nombre sur le nombre de **RDS. DataControl** objets que vous pouvez incorporer à l’aide de balises d’objet sur une page Web unique.  
  
 Lorsque vous définissez la **RDS. DataControl** de l’objet sur une page Web, utilisez différente de zéro **hauteur** et **largeur** valeurs telles que 1 (pour éviter l’inclusion d’espace supplémentaire).  
  
 Composants de client de Service de données à distance sont déjà inclus dans le cadre d’Internet Explorer 4.0 ; Par conséquent, vous n’avez pas besoin d’inclure un paramètre CODEBASE dans votre **RDS. DataControl** balise object.  
  
 Avec Internet Explorer 4.0 ou version ultérieure, vous pouvez lier aux données à l’aide de contrôles HTML et les contrôles ActiveX® uniquement s’ils sont marqués comme étant des contrôles de modèle de cloisonnement.  
  
> [!NOTE]
>  **Les utilisateurs de Microsoft Visual Basic** le **RDS. DataControl** est sécurisé pour le script et est utilisé uniquement dans les applications basées sur le Web. Une application cliente de Visual Basic n’a pas besoin pour elle.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés, méthodes et événements de l’objet DataControl (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [DataControl, exemple d’objet (VBScript)](../../../ado/reference/rds-api/datacontrol-object-example-vbscript.md)






















