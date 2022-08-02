# Backend-E-Commerce

## Description 

This project aims to showcase my ability in utilizing Express.js and Sequelize to build the back end for an e-commerce site.

![](./assets/images/demo-challenge-13.gif)


## Usage

In order to do this project, I modified a working Express.js API to use Sequelize to interact with a MySQL database.


```JavaScript
const { Model, DataTypes } = require('sequelize');

const sequelize = require('../config/connection.js');

class Tag extends Model {}

Tag.init(
  {
    id: {
      type: DataTypes.INTEGER,
      allowNull: false,
      primaryKey: true,
      autoIncrement: true,
    },
    tag_name: {
      type: DataTypes.STRING,
    },
  },
  {
    sequelize,
    timestamps: false,
    freezeTableName: true,
    underscored: true,
    modelName: 'tag',
  }
);

module.exports = Tag;
```

```Javascript
const router = require('express').Router();
const { Tag, Product, ProductTag } = require('../../models');

// The `/api/tags` endpoint

router.get('/', async (req, res) => {
  // find all tags
  try {
    const tagData = await Tag.findAll({
      include: [{ model: Product }],
    });
    res.status(200).json(tagData);
  } catch (err) {
    res.status(500).json(err);
  }
});
```

## Links

There is no deployed link but demo video available [here](https://www.youtube.com/watch?v=Ka_yISCDJ3E).

[Project Repository](https://github.com/zzzorigtbaatar/Backend-E-Commerce)

## Credits

* Jerome Chenette, UC Berkeley Extension Coding BootCamp

* https://www.npmjs.com/package/sequelize

* https://www.npmjs.com/package/express

## License

[LICENSE](/LICENSE)

## Contact

https://www.linkedin.com/in/zorizulkhuu/

https://github.com/zzzorigtbaatar