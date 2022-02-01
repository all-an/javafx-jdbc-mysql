![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=java&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-005C84?style=for-the-badge&logo=mysql&logoColor=white)
[![JavaFX - OpenjFx 17.0.2](https://img.shields.io/badge/JavaFX-OpenjFx_17.0.2-FF0000?style=for-the-badge)](https://)
[![Java  - JDBC](https://img.shields.io/badge/Java_-JDBC-006400?style=for-the-badge)](https://)
[![Development  - In Progress](https://img.shields.io/badge/Development_-In_Progress-ffff00?style=for-the-badge)](https://)
![Linkedin](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)


[Download Build](https://github.com/all-an/javafx-jdbc-mysql/tree/main/download)

### Estudo JavaFx / Jdbc / MySQL Project

### Projeto de estudos:

- Java ( Reforçando conhecimentos em OOP e programação funcional com Java )
- JavaFx
- JDBC
- MVC Pattern
- MySQL

```bash
 Build JAR file 
o Right click project name -> Export -> Java/Runnable JAR file -> Next 
o Select Main class 
o Select destination folder 
o Library handling: 3rd option

 Pack files 
o JAR file 
o db.properties 
o MySQL Connector 
o JavaFX SDK 
o Java SDK 
```

### Passando um controller (lambda) como argumento através do Consumer genérico <T> no método loadView()
#### Eliminando multiplos métodos, neste caso loadView2() comentado em /gui/MainViewController()

```java
@FXML
	private void onMenuItemDepartmentAction() {
		loadView("/gui/DepartmentList.fxml", (DepartmentListController controller) -> {
			controller.setDepartmentService(new DepartmentService());
			controller.updateTableView();
		});
	}
	
	@FXML
	public void onMenuItemAboutAction() {
		loadView("/gui/About.fxml", x -> {});
	}
	
	@Override
	public void initialize(URL uri, ResourceBundle rb) {
		// TODO Auto-generated method stub
		
	}
	
	private synchronized <T> void loadView(String absoluteName, Consumer<T> initializingAction) {
		try {
			FXMLLoader loader = new FXMLLoader(getClass().getResource(absoluteName));
			VBox newVbox = loader.load();
			
			Scene mainScene = Main.getMainScene();
			VBox mainVBox = (VBox)((ScrollPane)mainScene.getRoot()).getContent();
			
			Node mainMenu = mainVBox.getChildren().get(0);
			mainVBox.getChildren().clear();
			mainVBox.getChildren().add(mainMenu);
			mainVBox.getChildren().addAll(newVbox.getChildren());
			
			T controller = loader.getController();
            initializingAction.accept(controller);
		}
		catch (IOException e) {
			Alerts.showAlert("IO Exception", "Error loading view", e.getMessage(), AlertType.ERROR);
		}
	}
```

## Para consulta, revendo conceitos de Generics

<p align="center">
        <a href="https://www.linkedin.com/in/all-an/">
        <img align="center" width="633" height="551"  src="/images/type-parameter.png" />
</a>
</p>

