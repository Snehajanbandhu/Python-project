# Python-project
A Python mini-project implementing a retail inventory system to demonstrate practical use cases of Lists, Tuples, Sets, and Dictionaries.
 Task 1 Product Collection (List and Tuple)

#1. create a list of product containing 6 products names 

products = ["Laptop", "Smartwatch", "Keyboard", "mouse", "Scanner", "Printer"]
print("1.Original product list")
print(products)

2. # create a tuple name sample_product

# Tuple stores a product_name, price, category

sample_product = ["Laptop", 60000, "Electronics"]
print("\n Sample Product Tuple")
print(sample_product)

3. # print the 2nd and last product from the product list

print("\n Second product:", products[1])
print("last product:", products[-1])

4 # Append two new product names and print updated list

products.append("Headphone")
products.append("Earphone")

print("\n4 Updated Product List:")
print(products)

# Extra Convert sample_product into list, change its list and convert it back to a tuple

sample_product_list = list(sample_product)

# Change the price (index 1)
sample_product_list[1] = 52000

# Convert back to tuple
sample_product = tuple(sample_product_list)

print("\nExtra. Updated Sample Product Tuple:")
print(sample_product)



# Task 2: Categories (Sets)

# 1. Create a set of categories from the products list
# Use a parallel list to map each product to its category

product_categories = [
    "Electronics",
    "Electronics",
    "Audio",
    "Accessories",
    "Accessories",
    "Wearables",
    "Electronics",
    "Office"
]

categories_set = set(product_categories)

print("1. Unique Categories Set:")
print(categories_set)


# 2. Add a new category and demonstrate that duplicates are ignored
categories_set.add("Furniture")

print("\n2. After Adding Furniture:")
print(categories_set)

# Add an existing category again
categories_set.add("Electronics")

print("After Adding Electronics Again:")
print(categories_set)


# 3. Check whether a category exists in the set
print("\n3. Is Electronics in the Set?")
print("Electronics" in categories_set)

print("Is Clothing in the Set?")
print("Clothing" in categories_set)


# Extra (Optional): Count the total number of unique categories
print("\nExtra. Total Unique Categories:")
print(len(categories_set))


# Bonus: E-commerce Product Dictionary

product_details = {
    "product_name": "Laptop",
    "price": 55000,
    "category": "Electronics",
    "stock": 15
}

print("Product Details:")
print(product_details)

# Access individual values
print("Product Name:", product_details["product_name"])
print("Price:", product_details["price"])

# Update stock
product_details["stock"] = 12

print("Updated Product Details:")
print(product_details)


# Task 3: Product Pricing (Dictionaries)

# 1. Create a dictionary with at least 6 products and their prices
price_dict = {
    "Laptop": 55000,
    "Smartphone": 20000,
    "Headphones": 2500,
    "Keyboard": 1500,
    "Mouse": 800,
    "Smartwatch": 5000
}

print("1. Product Prices:")
print(price_dict)


# 2(a). Add a new product with its price
price_dict["Tablet"] = 15000

print("\n2(a). After Adding a New Product:")
print(price_dict)


# 2(b). Update the price of an existing product
price_dict["Laptop"] = 52000

print("\n2(b). After Updating Laptop Price:")
print(price_dict)


# 2(c). Remove a product by name
# Handle the case when the product does not exist
product_to_remove = "Mouse"

if product_to_remove in price_dict:
    del price_dict[product_to_remove]
    print(f"\n2(c). {product_to_remove} removed successfully.")
else:
    print(f"\n2(c). {product_to_remove} does not exist.")


# Demonstrate handling a product that does not exist
product_to_remove = "Camera"

if product_to_remove in price_dict:
    del price_dict[product_to_remove]
else:
    print(f"{product_to_remove} does not exist in the price dictionary.")


# 3. Calculate and print the average price of all products
if len(price_dict) > 0:
    average_price = sum(price_dict.values()) / len(price_dict)
    print("\n3. Average Product Price:", round(average_price, 2))
else:
    print("\n3. No products available to calculate the average.")


# Extra (Optional): Print the products with maximum and minimum prices
if price_dict:
    max_product = max(price_dict, key = price_dict.get)
    min_product = min(price_dict, key = price_dict.get)

    print("\nExtra. Product with Maximum Price:")
    print(max_product, "-", price_dict[max_product])

    print("Product with Minimum Price:")
    print(min_product, "-", price_dict[min_product])


# Task 4: Combined Operations

# Product list
products = [
    "Laptop",
    "Smartphone",
    "Headphones",
    "Keyboard",
    "Mouse",
    "Smartwatch"
]

# Product prices
price_dict = {
    "Laptop": 52000,
    "Smartphone": 20000,
    "Headphones": 2500,
    "Keyboard": 1500,
    "Mouse": 800,
    "Smartwatch": 5000
}

# Product categories
product_to_category = {
    "Laptop": "Electronics",
    "Smartphone": "Electronics",
    "Headphones": "Audio",
    "Keyboard": "Accessories",
    "Mouse": "Accessories",
    "Smartwatch": "Wearables"
}


# 1. Create a list of tuples named catalog
# Each tuple contains (product_name, price, category)

catalog = []

for product in products:
    if product in price_dict and product in product_to_category:
        catalog.append((
            product,
            price_dict[product],
            product_to_category[product]
        ))

print("1. Product Catalog:")
for item in catalog:
    print(item)


# 2. Create category_to_products dictionary
# Each category maps to a list of product names

category_to_products = {}

for product_name, price, category in catalog:
    if category not in category_to_products:
        category_to_products[category] = []

    category_to_products[category].append(product_name)

print("\n2. Products Grouped by Category:")
print(category_to_products)


# 3. Print all products belonging to the category
# that contains the maximum number of products


category_to_products = {
    "Electronics": ["Laptop", "Smartphone"],
    "Audio": ["Headphones"],
    "Accessories": ["Keyboard", "Mouse"],
    "Wearables": ["Smartwatch"]
}

if len(category_to_products) > 0:
    largest_category = max(
        category_to_products,
        key=lambda category: len(category_to_products[category])
    )

    print("Category with the maximum number of products:")
    print(largest_category)

    print("Products in this category:")
    for product in category_to_products[largest_category]:
        print(product)
else:
    print("No categories available.")
