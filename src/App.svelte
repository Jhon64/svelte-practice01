<script>
  import {
    Col,
    Container,
    Row,
    Card,
    CardBody,
    CardHeader,
    CardFooter,
    CardTitle,
    Input,
    Form,
    FormGroup,
    Label,
    Button
  } from "sveltestrap";
  import ListProduct from "./components/ListProduct.svelte";

  let product = {
    id: "",
    name: "",
    imageUrl:"",
    description: "",
    category: ""
  };



  $: listProduct = [
    {id: 0, name: "laptop toshiba", description: "is a laptop", category: "laptops"},
    {id: 1, name: "table ianix", description: "is a table", category: "tables"},
  ]


  const limpiar=e=>{
    product = {
      id: "",
      name: "",
      imageUrl:"",
      description: "",
      category: ""
    };
  }

  const onSubmitHandle = e => {
    let newProduct={
      id:listProduct.length,
      name:product.name,
      description:product.description,
      category:product.category,
      imageUrl:product.imageUrl
    }
    listProduct=listProduct.concat(newProduct)
    limpiar();
    e.preventDefault()
  }
</script>

<style>

</style>

<main>
  <Container class="mt-5">
    <Row>
      <Col sm="6" >
        <Card>
          <CardHeader>
            <CardTitle>Registro Productos</CardTitle>
          </CardHeader>
          <CardBody>
            <Form on:submit={onSubmitHandle}>
              <FormGroup>
                <Label>Product name</Label>
                <Input
                  placeholder="product name"
                  name="productName"
                  bind:value={product.name} />
              </FormGroup>
              <FormGroup>
                <Label>Product description</Label>
                <Input
                  bind:value={product.description}
                  placeholder="product description"
                  name="productDescription" />
              </FormGroup>
              <FormGroup>
                <Label>imageProduct</Label>
                <Input type="url"
                       placeholder="productUrl"
                       name="productUrl"
                       bind:value={product.imageUrl}/>
              </FormGroup>
              <FormGroup>
                <Label>Product category</Label>
                <select class="form-control " bind:value={product.category}>
                  <option value="laptops">Laptops</option>
                  <option value="Pc's">Pc's</option>
                  <option value="tables">Tables</option>
                </select>
              </FormGroup>
              <FormGroup>
                <Button class="btn-success" block size="md" type="submit">save</Button>
              </FormGroup>
            </Form>
          </CardBody>
        </Card>
      </Col>
      <Col sm="6" >

        <ListProduct listProduct={listProduct}></ListProduct>
      </Col>
    </Row>
  </Container>
</main>
