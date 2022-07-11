- # Database
	- ## gorm.io/gorm
- https://github.com/go-playground/validator 参数校验，可用于接口层的参数校验
- copier
	- when copy from a slice to slice, pass sclice's poiner:
		- ```go
		  	err = copier.Copy(&dubboScale.ProjectId, &scale.Project)
		  ```