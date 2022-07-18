# Lab 1.1

```yaml
1.Explore Google Cloud Console.
	 Done
```

```yaml
2.Setup a billing method on your google account.
3.Create a GCP project.
4.Assign your billing account to your project.
	5.Setup project budget.
6.Setup billing alerts.
	
	Hosted By Mostafa Elnaggar Brother Mohamed elNaggar
```

```yaml
7.Using cloud shell, list all projects and set default project.
```

![Screenshot from 2022-06-22 22-06-58.png](Lab%201%201%20f786275f4b5c4619ab8e921884ebd688/Screenshot_from_2022-06-22_22-06-58.png)

![Screenshot from 2022-06-22 22-22-03.png](Lab%201%201%20f786275f4b5c4619ab8e921884ebd688/Screenshot_from_2022-06-22_22-22-03.png)

```yaml
8.Install and configure gcloud SDK on your pc.
	 Done
```

```yaml
9.List all projects using gcloud SDK and set default project1.
```

![Screenshot from 2022-06-22 22-09-06.png](Lab%201%201%20f786275f4b5c4619ab8e921884ebd688/Screenshot_from_2022-06-22_22-09-06.png)

![Screenshot from 2022-06-22 22-24-31.png](Lab%201%201%20f786275f4b5c4619ab8e921884ebd688/Screenshot_from_2022-06-22_22-24-31.png)

# Lab 1.2

```bash
I.Create custom role named "my-custom-role-1" with the following permissions only:
– Iam.roles.get
– Iam.roles.list
```

![Screenshot from 2022-06-22 22-56-28.png](Lab%201%201%20f786275f4b5c4619ab8e921884ebd688/Screenshot_from_2022-06-22_22-56-28.png)

![Screenshot from 2022-06-22 22-54-50.png](Lab%201%201%20f786275f4b5c4619ab8e921884ebd688/Screenshot_from_2022-06-22_22-54-50.png)

```yaml
2.From Cloud console, Explore primitive and pre-defined roles and their permissions.
```

![Screenshot from 2022-06-22 22-59-16.png](Lab%201%201%20f786275f4b5c4619ab8e921884ebd688/Screenshot_from_2022-06-22_22-59-16.png)

![Screenshot from 2022-06-22 22-58-33.png](Lab%201%201%20f786275f4b5c4619ab8e921884ebd688/Screenshot_from_2022-06-22_22-58-33.png)

![Screenshot from 2022-06-22 23-02-28.png](Lab%201%201%20f786275f4b5c4619ab8e921884ebd688/Screenshot_from_2022-06-22_23-02-28.png)

```yaml
3.From Cloud console, Create a service account with id "my-first-serviceaccount".
```

![Screenshot from 2022-06-22 23-09-26.png](Lab%201%201%20f786275f4b5c4619ab8e921884ebd688/Screenshot_from_2022-06-22_23-09-26.png)

```yaml
4.From Cloud console, Assign the custom role "my-custom-role-1" to the service
account "my-first-serviceaccount"
```

![Screenshot from 2022-06-22 23-16-53.png](Lab%201%201%20f786275f4b5c4619ab8e921884ebd688/Screenshot_from_2022-06-22_23-16-53.png)

```yaml
5.Using gcloud,
I.List all roles on your project.

```

![Screenshot from 2022-06-22 23-21-20.png](Lab%201%201%20f786275f4b5c4619ab8e921884ebd688/Screenshot_from_2022-06-22_23-21-20.png)

```yaml
II.Describe the predefined role "roles/compute.viewer" and view its details & permissions
```

![Screenshot from 2022-06-22 23-27-05.png](Lab%201%201%20f786275f4b5c4619ab8e921884ebd688/Screenshot_from_2022-06-22_23-27-05.png)

```yaml
III.Describe the custom role "my-custom-role-1" and view its details & permissions.

```

![Screenshot from 2022-06-22 23-36-52.png](Lab%201%201%20f786275f4b5c4619ab8e921884ebd688/Screenshot_from_2022-06-22_23-36-52.png)

```yaml

IV.List all authenticated accounts.

```

![Screenshot from 2022-06-22 23-39-34.png](Lab%201%201%20f786275f4b5c4619ab8e921884ebd688/Screenshot_from_2022-06-22_23-39-34.png)

```yaml

V.Activate the service account "my-first-serviceaccount".

```

![Screenshot from 2022-06-22 23-44-30.png](Lab%201%201%20f786275f4b5c4619ab8e921884ebd688/Screenshot_from_2022-06-22_23-44-30.png)

```yaml

VI.List all authenticated accounts again.

```

![Screenshot from 2022-06-22 23-44-56.png](Lab%201%201%20f786275f4b5c4619ab8e921884ebd688/Screenshot_from_2022-06-22_23-44-56.png)

```yaml

VII.Using this service account, try to list all roles on your project.
```

![Screenshot from 2022-06-22 23-59-21.png](Lab%201%201%20f786275f4b5c4619ab8e921884ebd688/Screenshot_from_2022-06-22_23-59-21.png)

```yaml
VIII.Try to delete custom role "my-custom-role-1"

```

![Screenshot from 2022-06-23 00-01-03.png](Lab%201%201%20f786275f4b5c4619ab8e921884ebd688/Screenshot_from_2022-06-23_00-01-03.png)