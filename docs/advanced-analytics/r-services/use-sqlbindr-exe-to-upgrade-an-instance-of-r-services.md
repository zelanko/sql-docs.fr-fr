---
title: "Utilisez sqlBindR.exe pour mettre &#224; niveau une instance R Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server (starting with 2016 CTP3)"
ms.assetid: 4da80998-f929-4fad-a86f-87d09c1a79ef
caps.latest.revision: 15
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 8
---
# Utilisez sqlBindR.exe pour mettre &#224; niveau une instance R Services
Microsoft R Server pour Windows contient un nouvel outil, appelé **SqlBindR.exe**, qui peut être utilisé pour mettre à niveau les composants R pour une instance. Ce processus est appelé **liaison**, car il modifie le modèle de licence d’une instance SQL Server 2016 pour utiliser la nouvelle licence de support du cycle de vie des logiciels modernes Microsoft.

En règle générale, ce système de licence garantit que vos spécialistes des données utilisent toujours la dernière version de R. Pour plus d’informations sur les conditions et les avantages de la licence des logiciels Microsoft, consultez [Exécuter Microsoft R Server pour Windows](https://msdnstage.redmond.corp.microsoft.com/en-us/microsoft-r/rserver-install-windows?branch=r-server-nov16-dev).

Lorsque vous liez une instance, trois choses se produisent :
+ La stratégie de support de l’instance passe de la stratégie de support de SQL Server 2016 au nouveau contrat de licence des logiciels modernes Microsoft.
+ Les composants R associés à cette instance sont automatiquement mis à niveau avec chaque version, en même temps que la version R Server en cours, selon les nouvelles conditions de licence des logiciels modernes.
+ L’instance peut ne plus être mise à jour manuellement, excepté pour ajouter de nouveaux packages. 

Si vous décidez ultérieurement que vous souhaitez arrêter la mise à niveau de l’instance à chaque version, vous devez **annuler la liaison** de l’instance, puis désinstaller les composants Microsoft R Server comme décrit dans l’article [Exécuter Microsoft R Server pour Windows](https://msdn.microsoft.com/microsoft-r/rserver-install-windows). Lorsque le processus est terminé, les mises à niveau ultérieures de R Server n’affectent plus l’instance.

> [!NOTE] Le processus de mise à niveau est uniquement pris en charge pour les instances de SQL Server 2016 qui ont été corrigées avec la mise à jour cumulative 3.0.  
> 
> Si vous utilisez R Services dans SQL Server vNext, il est inutile d’appliquer cette mise à niveau. Les composants R sont automatiquement mis à niveau à chaque étape.

## <a name="how-to-upgrade-an-instance"></a>Comment mettre à niveau une instance


1. Exécutez le programme d’installation de Microsoft R Server sur l’ordinateur hébergeant l’instance que vous souhaitez mettre à niveau.
2. Lorsque l’installation est terminée, recherchez le dossier contenant l’outil **SqlBindR.exe**. L’emplacement par défaut est : `C:\Program Files\Microsoft\R Server\Setup`
2. Ouvrez une invite de commandes comme administrateur.
3. Tapez la commande suivante pour afficher la liste des instances disponibles : `SqlBindR.exe /list`
4. Exécutez la commande **SqlBindR.exe** avec l’argument */bind* pour spécifier le nom de l’instance à mettre à niveau. 
   Par exemple, pour mettre à niveau l’instance par défaut uniquement, tapez : `SqlBindR.exe /bind MSSQL14.MSSQLSERVER`

## <a name="how-to-downgrade-an-instance-of-r-services"></a>Comment passer à une version antérieure d’une instance R Services

Pour rétablir l’état d’une instance, vous devez exécuter l’outil SqlBindR pour supprimer la gestion de licences, puis réparer ou réinstaller l’instance.

1. Exécutez la commande **SqlBindR.exe** avec l’argument */unbind* et spécifiez l’instance. 
   Par exemple, la commande suivante rétablit l’instance par défaut pour se conformer à la gestion de licences SQL Server et au calendrier de mises à jour SQL Server :  `SqlBindR.exe /unbind MSSQL14.MSSQLSERVER`
2. Restaurez l’instance à son état d’origine en effectuant l’une des opérations suivantes :
    + Réparez l’instance. L’opération de réparation applique des mises à jour à toutes les fonctionnalités installées.
    + Désinstallez et réinstallez l’instance, puis appliquez toutes les versions de service. L’instance doit être redémarrée.
3. Une fois que R Server a été retiré, tous les packages qui ont été installés avec l’instance sont également supprimés. Ils doivent donc être réinstallés.

## <a name="requirements"></a>Spécifications
La mise à niveau est prise en charge uniquement pour les instances de SQL Server 2016 répondant aux exigences suivantes :
+ SQL Server 2016 SP1 ou version ultérieure
+ La mise à jour cumulative 3.0 (OD) a été appliquée

Actuellement, la mise à niveau est prise en charge uniquement au moyen de l’outil de ligne de commande. Une interface interactive sera fournie dans une version ultérieure.

## <a name="sqlbindrexe-command-syntax"></a>Syntaxe de commande sqlbindr.exe


### <a name="usage"></a>Utilisation

`sqlbindr [/list] [/bind <SQL_instance_ID>] [/unbind <SQL_instance_ID>]`

### <a name="parameters"></a>Paramètres

|Nom| Description|
|------|------|
|*list*| Affiche une liste de tous les ID d’instances de bases de données SQL sur l’ordinateur actuel|
|*bind*| Met à niveau l’instance de base de données SQL spécifiée vers la version la plus récente de R Server, et garantit que l’instance obtient automatiquement les mises à niveau ultérieures de R Server|
|*unbind*|Désinstalle la version la plus récente de R Server de l’instance de base de données SQL spécifiée, et empêche les mises à niveau ultérieures de R Server d’affecter l’instance|

### <a name="errors"></a>Erreurs

L’outil retourne les messages d’erreur suivants :

|Erreur|Résolution|
|------|------|
|Une erreur est survenue lors de la liaison de l’instance| L’instance n’a pas pu être liée. Contactez le support pour obtenir de l’aide.|
|L’instance est déjà liée| Vous avez exécuté la commande *bind*, mais l’instance spécifiée est déjà liée. Choisissez une autre instance.|
|L’instance n’est pas liée| Vous avez exécuté la commande *unbind*, mais l’instance que vous avez spécifiée n’est pas liée. Choisissez une autre instance.|
|ID d’instance SQL non valide| Vous avez peut-être mal tapé le nom de l’instance. Exécutez la commande à nouveau à l’aide de l’argument *list* pour voir les ID d’instance disponibles.|
|Aucune instance trouvée| Cet ordinateur ne dispose pas d’une instance de SQL Server R Services.|
|L’instance doit avoir une version compatible de SQL R Services (dans la base de données) installée.| Consultez https://go.microsoft.com/fwlink/?linkid=835761 pour plus de détails|
|Une erreur est survenue lors de l’annulation de la liaison de l’instance| L’annulation de la liaison de l’instance n’a pas pu être effectuée. Contactez le support pour obtenir de l’aide.|
|Une erreur inattendue s’est produite| Autres erreurs. Contactez le support pour obtenir de l’aide.  |
|Aucune instance SQL trouvée| Cet ordinateur ne dispose pas d’une instance SQL Server. |


## <a name="see-also"></a>Voir aussi

[Notes de publication de R Server](https://msdn.microsoft.com/microsoft-r/notes/r-server-notes)
